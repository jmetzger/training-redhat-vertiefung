# SELinux 

## sestatus

 * Zeigt an, obwohl selinux aktiviert und wie

## getenforce/ setenforce -> auf permissive setzen 

```
getenforce
setenforce 0
sestatus 
```

## Modi 

 * disabled 
 * enforcing (enabled)
 * permissive (enabled) 

## Persistente Konfiguration 

```
/etc/selinux/config
```
## Dateien mit context anzeigen

```
ls -laZ 
```

## Für nächsten Boot Context-Labels neu setzen 

```
# als root
cd / 
touch .autorelabel 
reboot
# Achtung relabeln kann dauern !!! durchaus 5 Minuten 
```
