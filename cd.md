# Navigieren mit cd

## Ins Heimatverzeichnis und Wurzelverzeichnis (C: unter Windows) wechseln 

```
# Ins Heimatverzeichnis wechseln 
# cd ohne alles 
cd 

# Ins Wurzelverzeichnis des Filesystems wechseln // Windows -> C:\
cd / 
```

## Wie in ein Verzeichnis wechseln (relativ und absolut) 

```
# relativ - nur in ein Unterverzeichnis meines bestehenden Verzeichnisses
cd etc 

# absolut - welchselt dort rein, egal wo ich bin 
cd /etc 
```

## Ins alte Verzeichnis wechseln 

```
cd /var/log
cd /etc
# Wechselt in /var/log zurück 
cd -
```
