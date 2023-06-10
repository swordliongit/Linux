
## Data Streams

Stream 0 = Standard Input(stdin)
Stream 1 = Standard Output(stdout)
Stream 2 = Standard Error(stderr)

### Dumping the content into a file and retrieving it back:
```sh
$: echo "hello world" > hello.txt
$: cat < hello.txt
hello world
```

## Standard Output and Standard Error( 2> &>)
\>

#### Redirecting Errors

Trying to cd into root gives us an error:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root
-bash: cd: /root: Permission denied
```

If we try to redirect the output to a txt file, we still get the error printed on the terminal:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root > error.txt
-bash: cd: /root: Permission denied
```

To avoid this, we have to use the standard error redirection ==2>==:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2> error.txt
```

```sh
swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied
```

Note that we can't use the error redirection to redirect standard output:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ echo "hello world" 2> hello.txt
hello world
```

#### Redirecting Errors and Output

To redirect both the errors and the output we have to use the ==&>==:
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root &> error.txt
```

---

### Scraping Output
==/dev/null==
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cd /root &> /dev/null
```

---

## Appending to the Output
If we use the double direction operator, the output won't overwrite the file but append to it.
==\>>==
==\2>>==
==&>>==
```sh
swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied

swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2>> error.txt
swordwsl@SWORD:~/bash_exp/scripts$ cd /root 2>> error.txt

swordwsl@SWORD:~/bash_exp/scripts$ cat error.txt
-bash: cd: /root: Permission denied
-bash: cd: /root: Permission denied
-bash: cd: /root: Permission denied
```