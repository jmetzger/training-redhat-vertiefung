# Use lvm 


## Exercise 

```
Server runterfahren und 3 Platte a 10 GB anlegen und zur maschine 
hinzufügen 

1. Platten identifizieren 
lsblk --fs
```

```
# Partition anlegen 
parted /dev/sdb
pvcreate /dev/sdb1
```

```
# physical volume erstellen 
pvcreate /dev/sdc
```

```
# alle volumegroups anzeigen
vgdisplay 
# neue Volumegroup erstellen 
vgcreate vg0 /dev/sdb1 /dev/sdc
```

```
lvcreate -L2G -n lv1 vg0
mkfs.xfs /dev/mapper/vg0-lv1
echo "/dev/mapper/vg0-lv1     /data                   xfs     defaults        0 0" >> /etc/fstab 
mkdir /data
# Testen 
mount -av 
```

```
# Tests mit data 
umount /data
# wer greift darauf zu 
fuser /data
cd ..
umount /data
cd /data 
ls -la 
touch .notmounted 
cd ..
mount /data 
cd /data
ls -la
```

```
# Testen, ob das nach Reboot geht 
reboot
```
