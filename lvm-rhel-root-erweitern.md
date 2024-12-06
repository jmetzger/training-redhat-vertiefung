# Rhel Root Partition erweitern

```
# 48G
df -h 
lvdisplay

# lsblk --fs
… sdd xxx G disk (ohne Partition)

# Verwaltungstabelle aufbringen 
pvcreate /dev/sdd

vgs
vgextend rl /dev/sdd 
# Volume group „rl1“ successfully extended
# vgs
rl1 … … … VSize <66g VFREE <50g
# lvs
rl1 … … … VSize <50g
LV     VG     Attr   LSize
root   rl1    …      <16g
…
lvextend –l +100%FREE /dev/rl/root
Logical volume successfully resized.
# lvs
vg0 … … … VSize <50g
LV     VG     Attr   LSize
root   vg0    …      <66g
…
# xfs_growfs /dev/rl/root
…
Data blocks changed from xxx to yyy
# df –l
…
/dev/mapper/vg0-root          XXX     YYY       66g  NN% /

```
