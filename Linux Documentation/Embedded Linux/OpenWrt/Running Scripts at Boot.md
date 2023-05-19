To run boot scripts, we have to add them to the ==/etc/rc.local== file, example rc.local:
```sh
# Put your custom commands here that should be executed once
# the system init finished. By default this file does nothing.
route add default gw 192.168.100.1 # add gateway to the device
lua /odoo_login.lua # run a lua script after everything is set
exit 0
```
