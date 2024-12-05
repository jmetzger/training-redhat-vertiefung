# SELinux (einfache Variante um postgresql-17 vom Maintainer unter SELinux laufen zu lassen 

## Verwendete Typen für Postgresql im Original von Redhat

```
Daten: postgresql_db_t
Logs: postgresql_log_t
Executable: postgresql_exec_t
Prozess: postgresql_t
```

## Verwendete Ports 

```
semanage port -l | grep postgres
postgresql_port_t              tcp      5432, 9898
```

## Gesetzten Filecontexts im Orignal Postgresql von Redhat 

  * Die Filecontexts existieren bereits als config auch wenn postgresql-server nicht installiert mit
(kommt selinux und Redhat - Installation mit)

```
./files/file_contexts:/usr/bin/(se)?postgres    --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/var/lib/pgsql(/.*)?      system_u:object_r:postgresql_db_t:s0
./files/file_contexts:/etc/postgresql(/.*)?     system_u:object_r:postgresql_etc_t:s0
./files/file_contexts:/var/lib/pgsql/.*\.log    system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/usr/bin/initdb(\.sepgsql)?       --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/var/lib/sepgsql(/.*)?    system_u:object_r:postgresql_db_t:s0
./files/file_contexts:/var/lib/postgres(ql)?(/.*)?      system_u:object_r:postgresql_db_t:s0
./files/file_contexts:/etc/rc\.d/init\.d/(se)?postgresql        --      system_u:object_r:postgresql_initrc_exec_t:s0
./files/file_contexts:/var/log/rhdb/rhdb(/.*)?  system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/var/log/postgresql(/.*)? system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/var/run/postgresql(/.*)? system_u:object_r:postgresql_var_run_t:s0
./files/file_contexts:/etc/sysconfig/pgsql(/.*)?        system_u:object_r:postgresql_etc_t:s0
./files/file_contexts:/var/log/postgres\.log.*  --      system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/usr/share/jonas/pgsql(/.*)?      system_u:object_r:postgresql_db_t:s0
./files/file_contexts:/var/lib/pgsql/logfile(/.*)?      system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/var/lib/pgsql/data/log(/.*)?     system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/usr/lib/postgresql/bin/.*        --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/var/log/sepostgresql\.log.*      --      system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/var/lib/pgsql/data/pg_log(/.*)?  system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/usr/lib/pgsql/test/regress(/.*)? system_u:object_r:postgresql_db_t:s0
./files/file_contexts:/usr/lib/systemd/system/postgresql.*      --      system_u:object_r:postgresql_unit_file_t:s0
./files/file_contexts:/usr/share/munin/plugins/postgres_.*      --      system_u:object_r:services_munin_plugin_exec_t:s0
./files/file_contexts:/usr/bin/pg_ctl   --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/usr/libexec/postgresql-ctl       --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/var/lib/sepgsql/pgstartup\.log   --      system_u:object_r:postgresql_log_t:s0
./files/file_contexts:/usr/bin/postgresql-check-db-dir  --      system_u:object_r:postgresql_exec_t:s0
./files/file_contexts:/usr/lib/pgsql/test/regress/pg_regress    --      system_u:object_r:postgresql_exec_t:s0
```

## Installation von postgres und Testlauf (ohne SELinux)

```
# Sourcen einrichten
```


```
dnf install -y postgresql17-server postgresql17-contrib
/usr/pgsql-17/bin/postgres
```

```
# Testlauf 
systemctl start postgresql-17 
systemctl status postgresql-17 
systemctl cat postgresql-17 | grep -i ^ExecStart 
```

## postgres binary testweise auf richtiges Labels setzen (postgresql_exec_t) 

  * Executable hat label postgresql_exec_t beim Starten gibt einen Domain Transfer, so dass
  * der Prozess unter postgresql_t läuft 

```
cd /usr/pgsql-17/bin/
chcon -t postgresql_exec_t postgres
```

```
# Starten und Prozess raussuchen
systemctl start postgresql-17
ps auxZ | postgres
```

```
# Läuft
```


## Datenverzeichnis auf falsche Label setzen -> var_t 

```
chcon -t var_t /var/lib/pgsql/17/data
```

```
systemctl stop postgresql-17
systemctl start postgresql-17
```

```
ACHTUNG: startet nicht, da Label Datenverzeichnis für prozess postgres nicht erlaubt
(Es muss: postgresql_db_t sein, ist aber var_t
```

```
# Entweder
cat /var/log/audit/audit.log | grep postgres
# oder
ausearch -c postgres
ausearch --comm postgres
# uns interessiert nur der type: AVC
```

```
# ---> denied
# AVC -> ACCESS VECTOR 
type=AVC msg=audit(1733391385.830:1195): avc:  denied  { write } for  pid=31310 comm="postgres" name="data" dev="dm-0" ino=35401409 scontext=system_u:system_r:postgresql_t:s0 tcontext=system_u:object_r:var_t:s0 tclass=dir permissive=0
```

## Label mit restorecon zurücksetzen 

   * Wichtige: Info SELinux bringt mit der Basisinstallation von Redhat bereits die richtigen Label-Definition mit.
   * Auch wenn postgres (Version von Redhat nicht installiert ist)
   * Diese Definitionen passen auch für die Files die mit postgresql17-server (vom Original Maintainer -> postgres) installiert werden, auch wenn die Filestruktur noch weitere Unterordner kennt (z.B. 17/data)

```
# -v verbose 
restorecon -vr /var/lib/pgsql/17/data 
```

```
restorecon -vr /var/lib/pgsql/17/data
Relabeled /var/lib/pgsql/17/data from system_u:object_r:var_t:s0 to system_u:object_r:postgresql_db_t:s0
```

```
# Jetzt startet postgresql-17 auch wieder
systemctl start postgresql-17
systemctl status postgresql-17
```

## Binary in der config mit richtigen Label setzen 

```
semanage fcontext -a -t postgresql_exec_t  "/usr/pgsql-(.*)/bin/postgres"
```

```
# testweise falsches Label setzen
chcon -t httpd_exec_t postgres
systemctl stop postgresql-17
# Startet nicht, weil httpd_t nicht auf das Datenverzeichnis von postgres zugreifen darf 
systemctl start postgresql-17
```

```
restorecon -vr /usr/pgsql-17/bin/
```

```
# Jetzt startet das ganze
systemctl start postgresql-17
```


## Anderes Datenverzeichnis setzen für SELinux und Postgresql 

```
semanage fcontext -a -t postgresql_db_t  "/db_data(/.*)?"
semanage fcontext -a -t postgresql_log_t  "/db_data/pg_log/(*.)log"

# Das kann man testen mit

ls -laZ /db_data
```






