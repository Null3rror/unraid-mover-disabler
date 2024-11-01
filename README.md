# unraid-mover-disabler
A simple command to disable Uraid's mover after each boot

---
Since Unraid doesn't retain modifications between reboots, you have to disable the mover after each reboot.
To do that automatically upon boot, simply add this: 
<br><br>
`sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"` 
<br>
to the end of your `/boot/config/go` to disable Unraid's mover.

At the end, your `/boot/config/go` should look like something like this:
```
#!/bin/bash

sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"
```

