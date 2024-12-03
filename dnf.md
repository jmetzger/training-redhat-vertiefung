# dnf

## Mögliche Paket anzeigen (die installiert sind und installiert werden können)

```
dnf list
# weitere Felder anzeigen 
dnf list --all 
```

## Installierte Pakete anzeigen 

```
dnf list --installed 
```

## Herausfinden, wie ein Paket heisst, dass ich installieren will

```
dnf list | grep mariadb 

```

## Ist ein Paket installiert 

```
dnf list --installed | grep mariadb 
```

## Nach einem Paket suchen 

```
dnf search mariadb 

```

## Infos zu einem Paket abrufen 

```
dnf info mariadb
```
