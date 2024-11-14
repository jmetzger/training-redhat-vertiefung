# Running Script in the background 

## Version with & (background task)

### Step 1: Create and run script 

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

### Step 2: Script starten  und beenden

```
endless.sh
# beend 
STRG + c
```
### Step 3: Im Hintergrund laufen lassen und abmelden

```
endless.sh &
# aus ssh abmelden
exit
```

### Step 4: in 2. Session - prüfen ob es noch läuft 

```
# ja, es läuft
ps aux | grep endless
```

## Version with & (background task) and nohup (no hangup)

### Step 1: Create and run script 

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
  echo $(date)"..hier ausgeben"
  sleep 2

done
```

```
chmod u+x endless.sh
```

### Step 2: Im Hintergrund mit nohup laufen lassen und abmelden

```
pwd
nohup endless.sh &
# aus ssh abmelden
exit
```

### Step 3: in 2. Session - prüfen ob es noch läuft 

```
# ja, es läuft
ps aux | grep endless
```


