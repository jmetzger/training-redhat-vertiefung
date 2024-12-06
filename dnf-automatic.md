# dnf automatic 

```
dnf install dnf-automatic
vim /etc/dnf/automatic.conf

download_updates = yes
apply_updates = yes

systemctl start dnf-automatic.timer 
systemctl enable dnf-automatic.timer

# 1x vorab testen
systemctl start dnf-automatic.service 

# Dauert einen Moment 
systemctl status dnf-automatic.service 
journalctl -eu dnf-automatic.service
```
