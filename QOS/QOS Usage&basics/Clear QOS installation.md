This article is step-by-step guide how to make clear installation of [QOS](QOS⚛️.md).

## Workstand
Our workstand is DT's Y4 processor

## Installation Process
1. Download latest `.iso` file from qos.com/download/LTS
2. Use any utility to flash this image to a flash drive e.g. Ventoy
3. Turn off your PC
4. Select this devices in BIOS and bootload from it
5. You will see QOS [Binary mode](Binary%20mode.md) with macros written on Desktop
6. Open terminal by `ctrl` + `alt` + `t`
### Making Partitions for future system
[Diskpart](Diskpart.md) in installation mode has more possibilities than diskpart in installed system
1. `qtc diskpart start fs/internal/dskprt/regex(ls, cd, mkdir, cppart, rwpart, ropart, fspart, tmp.modulepart, dump, pull, override).bin;` → initiating default command line utilities for further installation
2. `qtc diskpart run cppart init -rw:rootBIN -rw:QRoot -rw:ALR` → running cppart command for initiating QOS partitions with pre-defined access rules
3. `qtc diskpart run cd -c regex(sd/ESFS/ESFS.Q/QFS/tmp/cfg/diskpart/local/level/FS\fspart/rootBIN, sd/ESFS/ESFS.Q/QFS/tmp/cfg/diskpart/local/level/FS\fspart/QRoot, sd/ESFS/ESFS.Q/QFS/tmp/cfg/diskpart/local/level/FS\fspart/ALR);` → creating and changing working directory to specified with RegEx command
4. `qtc diskpart init regex(rootBIN, QRoot, ALR).fspart(-c -i -cont);` → initing partitions with flags -c(create), -i(initialize), -cont(contribute)
5. `qtc diskpart run dump -f sd/ESFS/ESFS.Q/QFS/tmp/cfg/sys/dump/rootBIN.dump -t sd/ESFS/$rootBIN$;` → Extracting [rootBIN](rootBIN.md) image from `.dump` file to specified directory on [ESFS](ESFS.md)
6. `qtc diskpart run dump -f sd/ESFS/ESFS.Q/QFS/tmp/cfg/sys/dump/QRoot.dump -t sd/ESFS/ESFS.Q/$QRoot$;` → the same with [QRoot](QRoot.md) partition
7. `qtc diskpart run dump -f sd/ESFS/ESFS.Q/QFS/tmp/cfg/sys/dump/ALR_prep.dump -t sd/ESFS/ESFS.Q/$ALR$;` → same with [ALR](ALR.md)
8. `qtc diskpart run override -w regex($rootBIN$, $QRoot$, $ALR$);` → overriding partitions with names in `$$`, which is using functions below to create partitions
>[!EXAMPLE] Functions
>frootBIN():; {
>	setPartName = `$rootBIN$`;
>	setPartDisc = `sd/ESFS/$rootBIN$`;
>	setPartTag = `#core #main #boot #load #ESFS`;
>	setPartMode = `$SYSTEM_MAIN_CORE_LOADER_partition`;
>	diskpart.assembly.partition(setPartName, setPartDisc, setPartTag, setPartMode);
>	dispart.formPart();
>	diskpart.addPart -t ESFS/ -o CorePart with.attribute -secured -sys -upd -restore -snap -enc -core;
>}
>fQRoot():; {
>	setPartName = `$QRoot$`;
>	setPartDisc = `sd/ESFS/ESFS.Q/$Qroot$`;
>	setPartTag = `#sys #user #q #secured`;
>	setPartMode = `$SYSTEM_MAIN_USER_PART`;
>	diskpart.assembly.partition(setPartName, setPartDisc, setPartTag, setPartMode);
>	dispart.formPart();
>	diskpart.addPart -t ESFS/ESFS.Q/ -o SysPart with.attribute -secured -user -sys -upd -enc;
>}
>fALR():; {
>	setPartName = `$ALR$`;
>	setPartDisc = `sd/ESFS/ESFS.Q/$ALR$`;
>	setPartTag = `#sys #tmp #q #CLEAR_ON_OFF`;
>	setPartMode = `$SYSTEM_MAIN_CACHE_PART`;
>	diskpart.assembly.partition(setPartName, setPartDisc, setPartTag, setPartMode);
>	dispart.formPart();
>	diskpart.addPart -t ESFS/ -o CorePart with.attribute -cache -sys -alr -enc -updstorage;
>}

9. `qtc diskpart write local:/QFS/ --config:dump -t local:/QFS/tmp/cfg/diskpart/config/planner/regex(restart,poweroff)/config.run;` → write planner configs to specified path
10. `qtc pcctrl schedule -pt restart; \n if fsLine(2).res() == Bool/'Done':; to run:; {qtc pcctrl run restart} \n else:; {qtc pcctrl run poweroff}` → schedule system's restart, but if restart is impossible, poweroff(restart is preferred than poweroff)