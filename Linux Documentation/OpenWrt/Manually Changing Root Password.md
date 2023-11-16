1. In Ubuntu, run this:
```sh
openssl passwd -1
```

2. Grab the encrypted password and open the /etc/passwd file and paste your password after the root: until :0
```sh
root:$1$pviTLYkm$x77xY5aP.LRaMx14lb2Eu/:0:0:root:/root:/bin/ash
```
