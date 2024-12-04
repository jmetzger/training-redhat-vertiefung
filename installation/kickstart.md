# Kickstart 

## After installation, you will find a kickstart in /root

```
cd /root
```

```
ls -la ana*
-rw-------. 1 root root 864 21. Nov 14:05 anaconda-ks.cfg
```

## Use it for it installation 

```
# Adjust boot-entry for installation (after bootup of installation iso)
kernel vmlinuz inst.ks=http://10.32.5.1/mnt/archive/RHEL-7/7.x/Server/x86_64/kickstarts/ks.cfg
```


## Referenz:

  * https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/installation_guide/sect-kickstart-howto#sect-kickstart-installation-starting-automatic
