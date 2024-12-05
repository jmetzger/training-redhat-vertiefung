# firewalld

## Install firewalld


```
# on centos/redhat firewalld should installed
systemctl status firewalld

# if not, just do it 
dnf install -y firewalld

```

## Is firewalld running ?
```
# is it set to enabled ?
systemctl status firewalld 
firewall-cmd --state
```

## Command to control firewalld 
  
  * firewall-cmd 

## Best way to add a new rule 
```
# Step1: do it persistent -> written to disk 
firewall-cmd --add-port=82/tcp --permanent  

# Step 2: + reload firewall 
firewall-cmd --reload 
```

## Zones documentation 

man firewalld.zones 

## Zones available 

```
firewall-cmd --get-zones 
block dmz drop external home internal public trusted work
```

## Active Zones 

```
firewall-cmd --get-active-zones
```

## Show information about all zones that are used 
```
firewall-cmd --list-all 
firewall-cmd --list-all-zones 
```


## Add Interface to Zone ~ Active Zone 

```
firewall-cmd --zone=public --add-interface=enp0s3 --permanent 
firewall-cmd --reload 
firewall-cmd --get-active-zones 
public
  interfaces: enp0s3

```
## Default Zone 

```
# if not specifically mentioned when using firewall-cmd
# .. add things to this zone 
firewall-cmd --get-default-zone
public

```

## Show services 
```
firewall-cmd --get-services
firewall-cmd --info-service=ssh
# Mit description
firewall-cmd --info-service=ssh --verbose 
```

## What ports a opened in a service 

```
# Example ssh 
cd /usr/lib/firewalld/services 
cat ssh.xml 
```

## Adding/Removing a service (Variante 1: nicht so schön)

```
firewall-cmd --permanent --zone=public --add-service=ssh
firewall-cmd --reload 
firewall-cmd --permanent --zone=public --remove-service=ssh
firewall-cmd --reload 
```

## Arbeiten mit runtime und permanenter config (für service) 

```
# nur für runtime setzen 
firewall-cmd --zone=public --add-service=http
# nur die runtime anzeigen
firewall-cmd --list-all
# nur die permanente konfiguration anzeigen
firewall-cmd --list-all --permanent
# Das wieder laden, was in der Konfiguration steht 
firewall-cmd --reload
```

## Service aktivieren und persistieren 

```
firewall-cmd --add-service=http --zone=public
# runtime
firewall-cmd --list-all
# permanent
firewall-cmd --list-all --permanent
# runtime-to-permanent
firewall-cmd --runtime-to-permanent

```


# firewall-cmd --permanent --zone=public --remove-service=ssh
```



## Add/Remove ports 
```
# add port
firewall-cmd --add-port=82/tcp --zone=public --permanent
firewall-cmd --reload

# remove port
firewall-cmd --remove-port=82/tcp --zone=public --permanent
firewall-cmd --reload
```

## Enable / Disabled icmp 
```
firewall-cmd --get-icmptypes
# none present yet 
firewall-cmd --zone=public --add-icmp-block-inversion --permanent
firewall-cmd --reload
```

## Working with rich rules 
```
# Documentation 
# man firewalld.richlanguage

# throttle connectons 
firewall-cmd --permanent --zone=public --add-rich-rule='rule family=ipv4 source address=10.0.50.10/32 service name=http log level=notice prefix="firewalld rich rule INFO:   " limit value="100/h" accept' 
firewall-cmd --reload # 
firewall-cmd --zone=public --list-all

# port forwarding 
firewall-cmd --get-active-zones
firewall-cmd --zone=public --list-all
firewall-cmd --permanent --zone=public --add-rich-rule='rule family=ipv4 source address=10.0.50.10 forward-port port=42343 protocol=tcp to-port=22'
firewall-cmd --reload 
firewall-cmd --zone=public --list-all
firewall-cmd --remove-service=ssh --zone=public

# 


# list only the rich rules 
firewall-cmd --zone=public --list-rich-rules

# persist all runtime rules 
firewall-cmd --runtime-to-permanent




```


## References 

  * https://www.ispcolohost.com/2016/07/25/blocking-outgoing-ports-with-firewalld/
  * https://www.linuxjournal.com/content/understanding-firewalld-multi-zone-configurations#:~:text=Going%20line%20by%20line%20through,or%20source%20associated%20with%20it.
  * https://www.answertopia.com/ubuntu/basic-ubuntu-firewall-configuration-with-firewalld/
