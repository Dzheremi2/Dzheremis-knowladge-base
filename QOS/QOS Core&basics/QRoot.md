QRoot is quantum [logical partition](Filesystem%20Hierarchy.md) that storage actual system files and data, **not core or kernel**.
User data stored on this partition in `/home/user_name` directory
QRoot is mounted to ==sd/ESFS/[ESFS.Q](ESFS.Q.md)/QFS/QRoot== but actually created at ==sd/ESFS/ESFS.Q==

>[!IMPRT] Important
>If QRoot is failed to load or it's working corrupted, [QOS](QOS⚛️.md) will automatically switched to QOS Rescue Mode by QRootStatusHandler(*core service*)

Here is QRoot's root hierarchy **↓**
### Hierarchy of QRoot partition
```mermaid
graph LR

root["/"] --> home["/home"]
home --> user_dir
root --> app["/app"]
app --> package_name --> comp_cache
package_name --> app_src
root --> sys["/sys"]
sys --> qtk
sys --> lib
root -.-> lib["/lib"]
lib --> shared_libs
root --> mnt["/mnt"]
mnt --> user_mounted_partitions
root --> tmp["/tmp"]
tmp --> temp_user_data
root --> proc["/proc"]
root --> internal[internal]
root -.-> cache["/cache"]
rbdata[rootBIN data] --> proc
ALR -- "QBit output before DPU" --> cache
ALR --> rbdata

class ALR,qtk internal-link;
```