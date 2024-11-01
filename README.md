# unraid-mover-disabler
A simple command to disable Uraid's mover after each boot

---
Since Unraid doesn't retain modifications between reboots, you have to disable the mover after each reboot.
To do that, simply add this `sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"` to the end of your `/boot/config/go` to disable Unraid's mover.

At the end, your `/boot/config/go` should look like something like this:
```
#!/bin/bash

sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"
```

