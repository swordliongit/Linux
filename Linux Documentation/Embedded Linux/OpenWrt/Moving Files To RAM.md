
Create partition in RAM
```shell
mount -t tmpfs -o size=10M tmpfs /mnt/
```
 Move the file into the partition:
```shell
 mv file /mnt/
```