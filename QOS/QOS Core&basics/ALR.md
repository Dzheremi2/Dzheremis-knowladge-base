ALR is very specific [FS](Filesystem%20Hierarchy.md) used as Quantum Cache(QC)
ALR used for data processing purposes, via [ESFS.Q](ESFS.Q.md) and [QTK](QTK.md)'s API to perform data transactions between CPU and QRoot directly, also used for QRoot's rootBIN access requests

### QRoot operations with ALR
>[!INFO]
>QRoot using ALR for "talking" with rootBIN. ALR provides all realizations for these, because QRoot, being Quantum Structured Filesystem cannot directly "talk" with binary storage without assisting of ALR 
1. Devices and core's info and funcs 
2. Core hardware dumps e.g CPU info, Disks info, Memory info e.t.c

>[!IMPRT] Warnings
>**→** ALR is mounting at [4th System initing step](System%20bootloading%20process.md), when kernel already loaded and QBitHandler started successfully
>**→** Unmounting ALR at the moment system is running will break [QRoot](QRoot.md) data transition with [rootBIN](rootBIN.md), which will cause system quantum mode crash and automatic entering to [QOS](QOS⚛️.md) Rescue Mode
>**→** ALR can be mounted to QRoot running instance as user preferred filesystem, so user can see processing files of ALR in File Manager. To mount ALR to QRoot as user you **must** specify mounting FS in ALR, because ALR has starting and killing billions of temporary filesystems, which provides system's correct work
>>[!EXAMPLE]
>>Examples
>>**→** `qtk diskpart -mount sd/ESFS/ESFS.Q/ALR/node.s910.handler -t /mnt/nodes910`
>>**→** `qtk diskpart -mount sd/ESFS/ESFS.Q/ALR/hidraw/*keyboards*/dev1:/mnt/dev1`