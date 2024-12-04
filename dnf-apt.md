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
