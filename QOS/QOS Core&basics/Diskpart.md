## What is diskpart?
Diskpart is basic [QOS](QOS⚛️.md) utility. One of three lowest utilities. Exists on [ESFS](ESFS.md) level as a part of the filesystem basic API

## What's purpose of diskpart?
Diskpart - Basic disk and [filesystem](Filesystem%20Hierarchy.md) control utility. It managing all filesystems including `ESFS, ESFS.Q, QFS, ALR`, all logical partitions `rootBIN, QRoot`, all external storages.
Every disk operation going through Diskpart, every file operation going through Diskpart

## How to use diskpart?
Diskpart used with `qtc` prefix if running out of [Quantum mode](Binary%20Mode.md).

### Basic diskpart commands
>[!EXAMPLE] Commands
>`qtc diskpart -mkdir <path/to/file>` **→** aliased as `mkdir` **→** Make a directory in described path or without path to create in directory where executed
>`qtc diskpart -mkfile <path/to/file>` **→** aliased as `cfile` **→** Creates file in described path or without path to create in directory where executed
>`qtc diskpart -rmdir <path/to/fil>` **→** aliased as `rmdir` **→** Removes directory in described path or without path to remove in directory where executed
>`qtc diskpart -rmfile <path/to/file>` **→** aliased as `rmfile` **→** Removes file in described path or without path to remove in directory where executed
>`qtc diskpart -mount <path/to/device:/path/to/partition>` **→** aliased as `mount` **→** Mounting described partition of described device to [QRoot](QRoot.md)/mnt
>`qtc diskpart -umount <path/to/mounted/partition>` **→** aliased as `umount` **→** Unmounting described partition from QRoot/mnt
>`qtc diskpart -cp -f <source/file> -t <destination/file>` **→** aliased as `cp` **→** Copying described file to described directory(-f and -t not used in aliased version) 

>[!EXAMPLE] Diskpart's partitioning commands
>`qtc diskpart allocate -physfs <var.FSTYPE> -on <path/to/target/device>` **→** setting default physical FS for target device
>`qtc diskpart allocate -logfs <var.FSTYPE> -on <path/to/target/device>` **→** setting default logical FS for target device
>`qtc diskpart part -cpart <path/to/target/device> -size <size_of_new_partition>` **→** creates new partition of selected size on selected device
>>[!WARNING] **↑**
>>Works only with binary storage devices
>
>`qtc diskpart part -dpart <path/to/target/device> -name <new_partition_name>` **→** create new partition on target device with described name
>>[!WARNING] **↑**
>>Works both binary and quantum partitions
>
>`qtc diskpart part -froze` **→** froze created partitions(Only for current session of creation)
>`qtc diskpart part -ufroze` **→** unfroze frozen partitions(Only for current session of creation)
>`qtc diskpart part -write` **→** Write created partitions to their specified places
>>[!IMPRT] Important **↑**
>>***This action isn't reversible and cannot be cancelled. ALL DATA FROM SPECIFIED PARTITIONS WILL BE FORMATTED*** 