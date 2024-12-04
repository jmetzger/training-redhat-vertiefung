# Redhat Vertiefung 

## Agenda

 1. Unterschiede Ubuntu / Redhat
    * [Unterschiede allgemein](unterschiede-ubuntu-redhat.md)
    * [Unterschiede dnf <-> apt](dnf-apt.md)

 1. Wartung und Aktualisierung
     * [Aktualisierung des Systems](dnf-update.md)
     * [Paketmanager dnf](dnf.md)
     * [Modules-Overview-Example](modules/overview.md)
     * [Upgrade Major-Version do-release-upgrade / leapp](major-upgrade-rhel-ubuntu.md)
     * [Walkthrough Leapp Upgrade RHEL 8.10 -> 9.4](upgrade/in-place/step-by-step.md)

 1. SELinux
     * [SELinux Überblick und Übung](selinux.md)
     * [SELinux neuen Port httpd](selinux-troubleshooting-centos.md)
     * [SELinux Policy für Postgresql17](selinux-policy-fuer-postgres17.md)

 1. Installation
     * [Automatische Installation mit kickstart](installation/kickstart.md)

 1. Systemadministration 
     * [Hostname setzen/abfragen](hostnamectl.md) 

## Backlog 

  1. Distributionen 
     * [Überblick](overview-distros.md)
  1. Verzeichnisse und Dateitypen 
     * [Verzeichnisaufbau](verzeichnisaufbau.md)
     * [Dateitypen](dateitypen.md) 
  1. Basisbefehle
     * [In den Root-Benutzer wechseln](sudo.md)  
     * [Wo bin ich ?](pwd.md)
     * [Praktische Ausgabe von langen Seiten - less](less.md) 
     * [Datei anlegen - touch](touch.md)
     * [Autovervollständen * und tab](autocomplete.md) 
     * [Welches Programm wird verwendet](which.md)
  1. Erweiterte Befehle (Nice to have) 
     * [Alias Befehle anzeigen](alias.md)
     * [Welche Bibliotheken verwendet ein ausführbares Programm](ldd.md)
     * [Ist ein Befehl extern, alias oder intern](type.md)
     * [History verwenden](history.md) 
  1. Dateien und Verzeichnisse
     * [Mit cd im System navigieren](cd.md)
     * [Verzeichnisse in Listenansicht mit versteckten Dateien anzeigen -> ls -la](list.md)
     * [Inhalt in Datei schreiben und anhängen](file-write-append.md)
     * [Verzeichnisse anlegen](mkdir.md)
     * [Verzeichnisse und Dateien löschen](file-dir-delete.md)
     * [Kopieren/Verschieben/Umbenennen von Dateien und Files](file-rename-copy-mv.md) 
     * [Arbeiten mit vi](vi.md)  
  1. Dateimanipulation/Unix Tools
     * [Anfang oder Ende einer Datei/Ausgabe anzeigen](head-tail.md)
     * [cat/head/tail-Beginn/Ende einer Datei anzeigen](cat-head.md)
     * [zcat - Inhalte einer mit gzip komprimierten Datei anzeigen](zcat.md)
     * [wc - Zeilen zählen](wc.md)
     * [Bestimmte Zeilen aus Datei anzeigen - grep](grep.md)
     * [Erweiterte Suche mit Grep](grep-extended.md)
     * [Finden von files nach Kriterien - find](find.md)
     * [Doppelte Leerzeichen aus Zeile rauslöschen](tr.md)
     * [Spalten auslesen mit awk](awk.md)
     * [Strings in datei ersetzen mit sed](sed.md)
  1. Backups
     * [Backup / Restore with tar](tar.md)
     * [Backup with tar / zstd](tar-zstd.md)
  1. Komprimierung
     * [Datei komprimieren](gzip.md)
  1. Prozesse
     * [Prozesse interaktiv mit top anzeigen](top.md)
     * [Prozesse anzeigen - ps/pstree -p](prozesse.md)
     * [Alle Prozesse eines Dienstes anzeigen](prozesse-dienst.md)
     * [Prozesse im Hintergrund laufen lasen](background-script.md)
  1. Festplattenbelegung
     * [Welche Verzeichnisse / Partitionen sind voll? du und df](df-du.md)  
  1. Benutzer, Gruppen und Rechte 
     * [Rechte/Benutzer/Gruppe](rechte.md) 
     * [Dateien für Benutzer und Gruppen](files-users-groups.md) 
     * [Benutzer anlegen](create-users.md) 
     * [sudo Benutzer erstellen](mod-user-sudo.md)   
  1. Logs/Loganalyse
     * [Logfile beobachten](tailf.md)
     * [Dienste debuggen](debug-service.md)
     * [Rsyslog](rsyslog.md)
     * [Journal analysieren](journalctl.md)
     * [Logrotate](logrotate.md)
  1. Dienste debuggen
     * [Dienste debuggen](debug-service.md)
  1. Variablen
     * [Setzen und verwenden von Variablen](variables.md) 
  1. Dienste/Runlevel(Targets verwalten) 
     * [Die wichtigsten systemctl/service](systemctl-service.md)
     * [Systemctl - timers](systemctl-timers.md)
     * [Systemctl - timer example](timer-example.md)
     * [Gegenüberstellung service etc/init.d/ systemctl](service-initd-systemctl.md)
     * [Default Editor systemctl setzen](default-editor-systemctl.md) 
  1. Systemd 
     * [Die wichtigen Tools für die Kommandozeile (ctl)](systemd-cli-tools.md)
  1. Systemadministration 
     * [ssh absichern](ssh-absichern.md)
  1. Partitionierung und Filesystem
     * [parted and mkfs.ext4](parted-mkfs.md)
  1. Boot-Prozess und Kernel 
     * [Grub konfigurieren](grub.md)
     * [Kernel-Version anzeigen](kernel-version.md) 
     * [Kernel-Module laden/entladen/zeigen](kernel-modules.md) 
  1. Hilfe 
     * [Hilfe zu Befehlen](help.md)
  1. Grafische Oberfläche und Installation 
     * [X-Server - Ausgabe auf Windows umleiten](xserver-windows-client.md)
     * [Installations-Images-Server](https://ubuntu.com/download/server#download) 
  1. Wartung und Aktualisierung
     * [Aktualisierung des Systems](dnf-update.md)
     * [Paketmanager dnf](dnf.md)
     * [Archive runterladen und entpacken](tar-download.md)
     * [Apache installieren (firewall und selinux)](apache-installieren-selinux-firewalld.md)
     * [mbr sichern mit dd](dd-mbr.md)
  1. Firewall und ports
     * [firewalld](firewalld.md)
     * [Scannen und Überprüfen mit telnet/nmap](nmap-telnet.md)
  1. Netzwerk/Dienste 
     * [IP-Adresse von DHCP-Server holen (quick-and-dirty)](dhclient.md) 
     * [Auf welchen Ports lauscht mein Server](lsof.md) 
     * [Interface mit nmtu-edit verwalten - schneller Weg](nmtui-edit.md)
     * [Netzwerkinterface auf der Kommandozeile einrichten](nmcli.md) 
     * [Scannen mit nmap](nmap.md)
  1. Mails
     * [lokale Mails installieren](local-mail.md)
  1. Bash/Bash-Scripting 
     * [Einfaches Script zur Datumsausgabe](script-date.md) 
     * [Ausführen/Verketten von mehreren Befehlen](multiple-commands.md)
     * [Example with date and if](01-date-if.md)
     * [Example with function and return value](02-function-return-value.md)
     * [Example with test and if](03-if.md)
     * [Example log function](04-log-function.md)
     * [Example Parameter auslesen](05-parameter-auslesen.md)
  1. Timers/cronjobs 
     * [Cronjob - hourly einrichten](cronjob-hourly.md)
     * [cronjob (zentral) - crond](crond.md) 
  1. Literatur 
     * [Literatur](literatur.md) 

## Backlog 

  1. Wartung und Aktualisierung
     * [Paketmanager yum](yum.md)

  1. Firewall
     * [Arbeiten mit firewalld](firewalld.md)

  1. Podman 
     * [Podman Walkthrough](podman.md)

  1. SELinux (Linux härten)
     * [SELinux](selinux.md)
    
  1. Tools/Verschiedens 
     * [Remote Desktop für Linux / durch Teilnehmer getestet](https://wiki.ubuntuusers.de/Remmina/)
     * [Warum umask 022 und 0002 ? - Geschichte](umask-002-022-why.md)
