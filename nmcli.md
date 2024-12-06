# nmcli 

## Verbindungen anzeigen 

```
nmcli connection show
# or 
nmcli conn show 
```

## Netzwerk-Interface statisch auf Server neu einrichten (server 2)

```
# muss in der Liste sichtbar sein 
nmcli con add type ethernet con-name enp0s9 ifname enp0s9 ipv4.method manual ipv4.addresses 192.168.1.2/24
nmcli con mod enp0s9 autoconnect yes

# verbindung neu hochziehen
nmcli con up enp0s9

# verbindungseigenschaften anzeigen
nmcli con show 

```

## Netzwerk-Interface statisch auf Server neu einrichten (server 3)

```
# muss in der Liste sichtbar sein 
nmcli con add type ethernet con-name enp0s9 ifname enp0s9 ipv4.method manual ipv4.addresses 192.168.1.3/24
nmcli con mod enp0s9 autoconnect yes

# verbindung neu hochziehen
nmcli con up enp0s9

# verbindungseigenschaften anzeigen
nmcli con show 

```

## Netzwerk-Interface modifizieren (server 3) 

```
# muss in der Liste sichtbar sein 
nmcli con add type ethernet con-name enp0s9 ifname enp0s9 ipv4.method manual ipv4.addresses 192.168.1.3/24
nmcli con mod enp0s9 autoconnect yes

# verbindung neu hochziehen
nmcli con up enp0s9

# verbindungseigenschaften anzeigen
nmcli con show 

# is ip gesetzt ?
ip a

```


## Ref:

  * https://www.howtoforge.de/anleitung/wie-man-eine-statische-ip-adresse-unter-centos-8-konfiguriert/
  * https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/networking_guide/sec-configuring_ip_networking_with_nmcli#permanently-configuring-a-device-as-unmanaged-in-networkmanager
