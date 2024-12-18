# systemctl / service 

## Welche Dienste sind aktiviert ?  

```
systemctl list-units --type=service
# oder
systemctl list-units -t service 
# oder
systemctl -t service 
```

## Wie finde ich einen service, der noch nicht aktiviert ist ? 

```
systemctl list-unit-files -t service | grep mariadb
```

## Wie starte und stoppe ich einen Dienst ?

```
systemctl start httpd
systemctl stop httpd 

```

## Wie ist die Konfiguration eines Dienstes ? 

```
systemctl cat sshd.service 

```

## Wie sehe ich den status eines Dienstes ? 

```
systemctl status sshd
systemctl status sshd.service 

# ältere Variante 
service sshd status 

```

## Wie kann ich einen Dienst deaktivieren ? 

```
## d.h. dienst wird beim nächsten Boot nicht gestartet

systemctl disable sshd.service
# oder
systemctl disable sshd 

```

## Wie sehe ich, ob eine Dienst aktiviert / deaktiviert ist ? 

```
systemctl is-enabled sshd.service 
echo $?
```

## Dienst aktivieren ?

```
systemctl enable sshd.service 
```





## Wie sehe ich, wie ein Service konfiguriert ist / Dienstekonfiguration anzeigen ? 

```
# z.B. für Apache2
systemctl cat apache2.service
```

## Wie kann ich rausfinden, wie die runlevel als targets heissen ?

```
cd /lib/systemd/system 
root@ubuntu2004-104:/lib/systemd/system# ls -la run*target
lrwxrwxrwx 1 root root 15 Jan  6 20:47 runlevel0.target -> poweroff.target
lrwxrwxrwx 1 root root 13 Jan  6 20:47 runlevel1.target -> rescue.target
lrwxrwxrwx 1 root root 17 Jan  6 20:47 runlevel2.target -> multi-user.target
lrwxrwxrwx 1 root root 17 Jan  6 20:47 runlevel3.target -> multi-user.target
lrwxrwxrwx 1 root root 17 Jan  6 20:47 runlevel4.target -> multi-user.target
lrwxrwxrwx 1 root root 16 Jan  6 20:47 runlevel5.target -> graphical.target
lrwxrwxrwx 1 root root 13 Jan  6 20:47 runlevel6.target -> reboot.target
```

## Welche Dienste sind enabled (preset) und auf dem System 
```
systemctl list-unit-files -t service
```

## Dienste bearbeiten 
```
systemctl edit sshd.service 
# Dann eintragen
[Unit]
Description=Jochen's ssh-server 
# Dann speichern und schliessen (Editor) 

systemctl daemon-reload 
systemctl status 
```

## Targets (wechseln und default) 

```
# Default runlevel/target auslesen 
systemctl get-default 
# in target wechseln 
systemctl isolate multi-user 
# Default target setzen (nach start/reboot) 
systemctl set-default multi-user 
```

## Alle Target anzeigen in die ich reinwechseln kann (isolate) 

```
# Redhat / centos  
grep -r "AllowIsolate" /usr/lib/systemd/system 
/usr/lib/systemd/system/reboot.target
...
...
...
systemctl isolate reboot.target 
```

## Dienste maskieren, so dass sie nicht gestartet werden können 

```
systemctl mask apache2
# kann jetzt gestartet werden
systemctl start apache2

# de-maskieren 
systemctl unmask apache2 
# kann wieder gestaret werden
systemctl start apache2
```

## systemctl - Diverse Beispiele 
```
# Status eines Dienstes überprüfen 
service sshd status 
systemctl status sshd 

# Wie heisst der Dienst / welche Dienste gibt es ? (nur wenn der service aktiviert ist). 
systemctl list-units -t service 
# für apache
systemctl list-units -t service | grep ^apache
# die Abkürzung 
systemctl -t service | grep ^apache

# Wie finde ich einen service, der noch nicht aktiviert ist ? 
systemctl list-unit-files -t service | grep ssh

# Dienst aktivieren
systemctl enable apache2 
# Ist Dienst aktiviert 
systemctl is-enabled apache2
enabled
echo $?
0 # Wenn der Dienst aktiviert ist 

# Dienst deaktivieren (nach Booten nicht starten)
systemctl disable apache2
systemctl is-enabled 
disabled
echo $?
1 # 1 wenn nicht aktiviert

# Rebooten des Servers
# verweist auf systemctl 
reboot
systemctl reboot
shutdown -r now  

# Halt (ohne Strom ausschalten) 
halt
systemctl halt 
shutdown -h now 

# Poweroff 
poweroff
systemctl poweroff 
```


## systemctl Cheatsheet 

  * https://access.redhat.com/sites/default/files/attachments/12052018_systemd_6.pdf



