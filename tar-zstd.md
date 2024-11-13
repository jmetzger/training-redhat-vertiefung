# tar with zstd

## Simple with default compression (3) 

```
tar cvf _etc.foobar.tar.zst --zstd /etc
```

## Use higher compression 

```
# send result of tar to stdout 
tar cvf - /etc | zstd -15 > _etc.mega.tar.zst
```
