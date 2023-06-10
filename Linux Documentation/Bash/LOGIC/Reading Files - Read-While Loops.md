
To achieve this behaviour we have to use read while loops. We pass a file name to the program and it iterates over each line while printing them:
```sh
$ ./readwhile.sh performance/memory.log

total        used        free      shared  buff/cache   available
Mem:        7962952      337212     7452184        2280      173556     7406660
Swap:       2097152           0     2097152
```

```sh
#!/bin/bash

while read line; do
    echo "$line"
done < "$1"

exit 0 
```
**Notes:**
Positional parameter $1 gets directed as a standard input to the while loop which in turn passes it to the input of the read command, that is the "line", then the file gets dissected into separate lines by Shell and printed out using the echo.

### ==Common Mistake==

This syntax redirects the standard input to the read command and will loop forever. Instead we need to redirect the standard input to the while command.
```sh
#!/bin/bash

while read line < "$1"; do
    echo "$line"
done 

exit 0 
```


## Reading Output of Commands - Process Substitution
[[Reading Output of Commands - Process Substitution]]

Output of a command can be redirected using process substitution that will end up passing to the while loop as a file and will be dissected by the read command.
```sh
#!/bin/bash

while read line < "$1"; do
    echo "$line"
done < <(ls $HOME)

exit 0 
```

```sh
$ ./rw-process-sub.sh

bash_exp
firmware-experiments
firmware-mod-kit
gcc
hello.c
openwrt
openwrt-testing
tftpclient
uboot
```