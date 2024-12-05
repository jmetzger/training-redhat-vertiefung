# SELinux 



## Gesetzten Filecontexts im Orignal Postgresql von Redhat 

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
