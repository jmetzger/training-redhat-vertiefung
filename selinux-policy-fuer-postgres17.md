# Selinux Policy für Postgres17 

```
https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/using_selinux/writing-a-custom-selinux-policy_using-selinux#creating-and-enforcing-an-selinux-policy-for-a-custom-application_writing-a-custom-selinux-policy
# Neue Policy zu erstellen 
dnf install -y policycoreutils-devel
dnf install -y curl nc rpm-build 
# Erste Schritt: läuft prozess unter selinux 
ps auxZ | grep pgsql 
# unconfined - not running under selinux 
/usr/pgsql-17/bin/postgres -D /var/lib/pgsql/17/data/
unconfined_u:unconfined_r:unconfined_t
```

## Fix für Rocky 9 

```
"quick-and-dirty-fix" für Rocky:
sudo sed -i s/"\$rltype"/".5"/g /etc/yum.repos.d/rocky*.repo
# Kudos go to D. 
```

```
# Erstellt die entsprechenden Files 
# generate hat verschiedene Optionen 
# Der Dienst muss laufen 
sepolicy generate --init /usr/pgsql-17/bin/postgres
```

```
# Danach alles erstellen mit
./postgres.sh
```

## Referenzen

  * https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/9/html/using_selinux/writing-a-custom-selinux-policy_using-selinux#creating-and-enforcing-an-selinux-policy-for-a-custom-application_writing-a-custom-selinux-policy
