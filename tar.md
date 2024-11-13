# tar 

## Sichern / Backup 

```
cd /usr/src
tar cfvz _etc.20220617.tar.gz /etc
# war das archivieren erfolgreich // dann 0 
echo $? 
tar tf _etc.20220617.tar.gz
```


## Entpacken (Vorbereitung) 

```
mkdir foo
mv _etc.20220617.tar.gz foo
cd foo
```



## Entpacken (Variante 1)

```
tar xvf _etc.20220617.tar.gz

# Aufräumen
rm -fR etc/
```

## Entpacken (Variante 2) 

```
tar tf _etc.20220617.tar.gz

# Achtung Fehler - weil falscher Pfad 
tar xvf _etc.20220617.tar.gz etc/sysctl.d/99-sysctl.conf /etc/services
echo $?

# So geht's 
tar xvf _etc.20220617.tar.gz etc/sysctl.d/99-sysctl.conf etc/services
ls -la
```

## Entpacken (Variante 3) - direkt in ein bestimmtes Verzeichnhis

```
tar tf _etc.20220617.tar.gz
tar xvf _etc.20220617.tar.gz -C / etc/sysctl.d/99-sysctl.conf etc/services
```


## Referenz:

  * https://linuxconfig.org/how-to-create-incremental-and-differential-backups-with-tar

