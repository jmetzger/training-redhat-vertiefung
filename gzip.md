# Gepackte Datei anzeigen

## zcat 

```
zcat /var/log/syslog.2.gz 
```

## Übung komprimieren 

```
Phase 1:  Komprimieren 

cd /var/log 
cat messages | grep 'Nov 13' | gzip  
cat messages | grep '^Nov 13' | gzip > /usr/src/messages.gz

Phase 2: Entpacken 
gzip -d messages.gz
# or
gunzip messages.gz
```
