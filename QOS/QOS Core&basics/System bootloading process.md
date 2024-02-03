## There all system bootloading steps from power button pressed to LoginD session visualized

0. Power button pressed, sent UEFI signal for system bootloading
	1. UEFI started boot.efi file on disk for running system initing as in Linux or Windows
	2. boot.efi file successfully completed it's purpose, started system initialization
1. Basic system initialization
	1. boot.efi ordered filesystem initiation
	2. On sd created partition [ESFS](ESFS.md)
	3. ESFS requested creating and mounting of rootBIN partition
	4. [rootBIN](rootBIN.md) partition created and mounted
	5. Setting core initiation
2. SysCore initiation
	1. boot.efi file requested initing of bootload script for ESFS
	2. ESFS starting bootload script
	3. Bootload script started core assembling 
	4. Core assembled
	5. Starting CoreHandler and CoreHandlerD binary services for future initiation
	6. Marking bootload script as completed **→** closing UEFI boot.efi file process, exiting UEFI
3. Quantum Initialization 1st step
	1. CoreHandler sent core request for assembling Kernel(Control Quantum memory by QBitHandler and QBitHandlerD)
	2. Kernel assembled successfully 
	3. Kernel started QBitHandler and QBitHandlerD
	4. QBitHandler setting [ESFS.Q](ESFS.Q.md) bootstrapping
	5. ESFS.Q bootstrapped successfully 
	6. Changing QBitHandler from `init` to `tracking` mode
	7. Initing ESFS.Q bootload script
4. Quantum Initialization 2nd step
	1. ESFS.Q's bootload script started [QFS](QFS.md) bootstrapping from `sd/ESFS/rootBIN/sys/core/fs/QFS/bootstrap.init`
	2. QFS bootstrapped successfully
	3. ESFS.Q initing [ALR](ALR.md) bootstrapping
	4. Bootloader script started ALR bootstrapping from `sd/ESFS/rootBIN/sys/core/fs/ALR/bootstrap.init`
	5. ALR successfully bootstrapped
	6. Setting up [Filesystem Hierarchy](Filesystem%20Hierarchy.md)
	7. Marking 4 step as completed, initing `sd/ESFS/sys/core/fs/sytem/QRoot.init`
5. Initing [QRoot](QRoot.md)
	1. Getted task for mounting QRoot, but partition does not exist yet, sending QRoot assembling reqest to ESFS.Q
	2. QRoot partition assembled successfully
	3. Marking QRoot as mount candidate
	4. Mounting QRoot
	5. Initing `sd/ESFS/ESFS.Q/rootBIN/sys/system/init.objqsrc`
	6. Starting system
6. System-side services initiation
	1. Starting HandlerService and HandlerServiceD
	2. Starting all services from `sd/ESFS/ESFS.Q/QFS/QRoot/sys/services/init/*.service`
	3. Requesting library initiation
	4. Initing libs from `sd/ESFS/ESFS.Q/QFS/QRoot/lib/`
	5. Starting [QTK](QTK.md)
	6. Initing all QTK's services
	7. Starting QTKHandler and QTKHandlerD
	8. Marking LoginD as initiation condidate
7. Finishing up, showing LoginD
	1. Launching LoginD service
	2. Initing user's workspace from `QRoot/home/`
	3. Stopping all `.init` services launched from `sd/ESFS/ESFS.Q/rootBIN/sys/core/fs/*`
	4. Marking system initiation as finished, setting registry variable `0/system/init/init.reg` --> from `running` to `done`
	5. Tasking LoginD show up procedure
	6. Showing LoginD up

 