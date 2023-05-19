
After using firmware-mod-kit to extract the firmware then we can do:
```sh
swordwsl@SWORD ~/firmware-mod-kit (master)> sudo chroot ~/firmware-mod-kit/fmk/rootfs/ /bin/sh
```

It will be like we are in the actual busybox shell of the router and we can install packages from there.


opkg lock error fix:
```sh
mkdir -p /var/lock
```