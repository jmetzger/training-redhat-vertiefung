# Diff & Patch 

## Walkthrough 


```
cd
nano hello.c
```

```
#include <stdio.h> 

int main() {
printf("Hello World\n");
}
```

```
cp hello.c hello_new.c
```

```
nano hello_new.c
```

```
#include <stdio.h>

int main(int argc, char *argv[]) {
printf("Hello World\n");
return 0;
}
```

```
diff -u hello.c hello_new.c > hello.patch
cat hello.patch
```


```
patch < hello.patch
```

