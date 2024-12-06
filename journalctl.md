# Journalctl 

## Show all boots 

``` 
 journalctl --list-boots
 0 3c3cf780186642ae9741b3d3811e95da Tue 2020-11-24 14:29:44 CET▒<80><94>T>
lines 1-1/1 (END)
```

## Show boot log 

```
journalctl -b 
```


## Journal persistent 

  * Normalerweise (auf den meisten Systemen), überlebt das Journal kein Reboot 
 
```
# persistent setzen
# Achtung: in /etc/systemd/journald.conf muss Storage=auto gesetzt sein
# Dies ist auch der Default - Fall 
# Achtung Achtung: Alle gezeigten Einträge mit # am Anfang sind die Default-Werte (in journald.conf) 
mkdir /var/log/journal 
systemctl restart systemd-journal-flush.service
systemctl restart systemd-journald.service 
```

## Restrict how much is logged / data 

```
# in /etc/systemd/journald.conf 
SystemMaxUse=1G 
```

## journalctl 

```
journalctl -u sshd 

# Nicht von Anfang, sondern die letzten Zeilen anzeigen 
journalctl -eu sshd
```

## journalctl - ausgabe json 

```
# sehr schön um alle felder zu sehen 
journalctl -o json-pretty 
```

## journalctl - konkreten Prozess anzeigen 

```
journalctl _PID=5
```

## journalctl - was gibt es für Felder 

```
journalctl -o json-pretty 
journalctl -u sshd.service -o json-pretty
```


## journalctl - mit Zeitangaben 

```
# alles seit gestern 
journalctl --since yesterday 
journalctl --since now 
journalctl --since today
# mit datum -> hier wichtig, dass richtige format
# Mindestens Tag oder Tag und Uhrzeit (ohne sekunden)
# nur Stunde geht nicht
journalctl --since "2022-08-17 00:05"

# bis heute 09:45 
journalctl --since yesterday --until "09:45"
```

## journalctl - immer die neuesten Infos ausgeben (wie bei tail -f) 

```
journalctl -f -u apache2.service 
```

## Help-pages 

```
man journalctl
man systemd.journal-fields
```


