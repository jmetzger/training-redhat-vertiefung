# Running Script in the background 

## Step 1: Create and run script 

```
cd /usr/local/bin 
nano endless.sh
```

```
let i=0
while true
do
  let i=i+1
  echo $(date)"..jetzt.."$i >> /var/log/endlosscheife.log
  sleep 2

done
```

```
chmod u+x endless.sh
```

## Step 2: Script starten  und beenden

```
endless.sh
# beend 
STRG + c
```

