# Replace string across file (in place) 

```
# good test it before on stdout without inplace param -> -i
cp -a /etc/ssh/sshd_config /etc/ssh/sshd_config_test
sed "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config_test | less
# then in place 
sed -i "s/PasswordAuthentication no/PasswordAuthentication yes/g" /etc/ssh/sshd_config_test
```
