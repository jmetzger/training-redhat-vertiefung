# Unterschied apt und dnf

## apt purge/remove vs. dnf remove package

```
dnf remove
# mach das gleich wie apt purge + apt autoremove
# Löschen der Konfigrationsdateien
# d.h. Deinstallieren der Abhängigkeiten
```

## Weitere Informationen zu installiertem Paket 

```
apt show curl 
dnf info curl
```

## Installierte Dateien durch Paket 

```
dpkg -L package-name  
rpm -ql openssh-server
```

## Update (Patchen des Systems) 

```
apt update
apt upgrade
apt dist-upgrade 
```

```
dnf check-update
dnf update
```

## Download  

```
dnf download openssh-server
apt download openssh-server
```

```
cd /usr/src
dnf download openssh-server

mkdir packagecontents; cd packagecontents
rpm2cpio ../openssh-server*.rpm | cpio -idmv
ls -la 

# For Reference: the cpio arguments are

# -i = extract
# -d = make directories
# -m = preserve modification time
# -v = verbose
```
