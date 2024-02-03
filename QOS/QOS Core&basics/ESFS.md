## What is ESFS

**ESFS(Extended Storage FileSystem) is a basic Filesystem used in [QOS](QOS⚛️.md) and developed for general binary data storage purposes**
**[ESFS](Filesystem%20Hierarchy.md) support binary data storage devices with size up to 100TB**

>[!INFO] Info
>ESFS developed in 2025 by Michael Erranger for data center's purposes and for easy data backup

>[!NOTE] Note
>ESFS support extensions that assigned as another filesystems thats are derivatives of ESFS
>>[!EXAMPLE] Examples
>>*ESFS.M*
>>*ESFS.R*
>>*ESFS.S*
>>*ESFS.RS*


>[!IMPRT] B-Tree
>ESFS **isn't** [b-tree supported filesystem](ESFS.Q.md)

All binary data storage devices and QOS's logic partition rootBIN are mounted to ESFS physical partition