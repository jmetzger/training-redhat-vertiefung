# mbr sichern 

  * Nur bei msdos mbr, nicht gpt

## Walktrough 

```
# master boot record sichern 
dd if=/dev/sda bs=512 count=1 of=mbr.img

# Zurückspielen
dd if=mbr.img bs=512 count=1 of=/dev/sda
```
