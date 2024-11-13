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

