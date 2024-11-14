# df und du (Disk Free und Disk Usage)

## Ist meine Platte voll 

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

