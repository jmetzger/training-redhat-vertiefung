# Timer Example

## Step 1: Create script 

```
cd /usr/local/bin 
nano script.sh 
```


```
#!/bin/bash
TAG='FREITAG'
echo " ---- " 
date 
echo $TAG 
```

## Step 2: Service-Unit für script 

```
systemctl edit --full --force myscript.service
```

```
[Unit]
Description=myscript 

[Service]
Type=oneshot 
ExecStart=/usr/local/bin/script.sh
```

```
systemctl start myscript.service 
```


## Step 3: Timer-Unit für script 

```
systemctl edit --full --force myscript.timer
```

```
[Unit]
Description=myscript timer 

[Timer]
OnBootSec=80
OnCalendar=*:0/2

[Install]
WantedBy=multi-user.target
```

## Step 4: Timer aktiveren 

```
systemctl enable myscript.timer
systemctl start myscript.timer 
systemctl list-timers 
```

