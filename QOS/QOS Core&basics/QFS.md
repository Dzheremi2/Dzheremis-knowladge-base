[QFS](Filesystem%20Hierarchy.md) is ***logical*** filesystem, mountable to [ESFS.Q](ESFS.Q.md) partition and provides [QOS](QOS⚛️.md)-specific APIs and functionalities 
QFS is fully integrated with [QTK](QTK.md) and wouldn't work without QTK inited with system core 

QFS provides basic Input/Output functions via qtk.filesystem.* API
>[!WARNING] Because of this ↑
>QFS cannot be used with any other Quantum supported filesystem different of ESFS.Q and without QTK installed

>[!INFO] Info
>QFS is mounting to ESFS.Q partition with [ESFS](ESFS.md)-specific internal driver function. There is no any mount point(Mounted directly to `ESFS/ESFS.Q` physical partition, cannot be visualized as file or something like this)