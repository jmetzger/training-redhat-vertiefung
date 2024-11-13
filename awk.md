# Example awk 

## /etc/passwd

```
# use ':' as seperator 
cat /etc/passwd | awk -F: '{print $6 ":" $1}'
```
