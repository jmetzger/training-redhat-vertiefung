# df und du (Disk Free und Disk Usage)

## Ist meine Platte voll ?

```
# Alle Partitionen 
df -h
# nur root partition
df -h /
# eine bestimmte Partition
df -h /dev/sda1
# ein file, welche partition ist das 
df -h /etc/hosts 
```

## Welche Verzeichnisse sind besonders voll ? 

```
# zeigt top-level verzeichnisse 
du -h --max-depth=1 / 

# zeigt directories für /var/log an
du -h --max-depth= 1 /var 
```

