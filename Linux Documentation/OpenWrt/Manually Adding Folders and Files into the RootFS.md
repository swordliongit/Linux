1. Using the firmware-mod-kit, open the build-firmware.sh and navigate to this lines:
```sh
# if blocksize var exists, then add '-b' parameter
if [ "$FS_BLOCKSIZE" != "" ]; then
		BS="-b $FS_BLOCKSIZE"
		HR_BLOCKSIZE="$(($FS_BLOCKSIZE/1024))"
		echo "Squashfs block size is $HR_BLOCKSIZE Kb"
fi
$SUDO $MKFS "$ROOTFS" "$FSOUT" $ENDIANESS $BS $COMP $MKFS_ARGS
```

2. Add this line above the last line here. Specify your folders, save and exit the file then build your firmware:
```sh
mv -R "$ROOTFS/odoo_project" "$ROOTFS/etc/"
```

```sh
# if blocksize var exists, then add '-b' parameter
if [ "$FS_BLOCKSIZE" != "" ]; then
		BS="-b $FS_BLOCKSIZE"
		HR_BLOCKSIZE="$(($FS_BLOCKSIZE/1024))"
		echo "Squashfs block size is $HR_BLOCKSIZE Kb"
fi
mv -R "$ROOTFS/odoo_project" "$ROOTFS/etc/"
$SUDO $MKFS "$ROOTFS" "$FSOUT" $ENDIANESS $BS $COMP $MKFS_ARGS
```