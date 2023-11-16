
## Using WSL UBUNTU (GD25Q127C flash rom)

1. Connect the CH341 spi programmer
2. Admin Powershell -> usbipd wsl list
3. usbipd wsl attach --busid <idofdevice>
4. Ubuntu terminal -> sudo flashrom -c GD25Q127C/GD25Q128C --programmer ch341a_spi -r flashrom.bin (-w writes the .bin file into the flash)