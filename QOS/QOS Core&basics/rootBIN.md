rootBIN is the binary [logical partition](Filesystem%20Hierarchy.md) which stores system's core source. Used as basic partition for system initialization. Mounted to [ESFS](ESFS.md) partition directly

### Hierarchy of rootBIN partition

```mermaid
graph LR

root["/"] --> sys["/sys"]
root --> tmp["/tmp"]
root --> cache["/cache"]
root --> Internal["/internal"]
root --> IO["/io"]
root -.-> ALR["/ALR"]
alr["ALR"] --> ALR
sys --> dev[dev]
sys --> core
sys --> local
sys --> global
sys --> internal --> qbits
sys -.-> registry
QRoot <--> alr --> registry
sys --> qb -.-> qbits["QBit's binary files(store internal QBit metadata)"]

class QRoot,alr internal-link;
```

### rootBIN reserved space
```mermaid
pie title QBit metadata reserved size

"QBits metadata" : 4
"Core in /sys/core" : 80
"Snapshots in /internal" : 16
```