# unraid-mover-disabler
Since Unraid doesn't retain modifications between reboots, you have to disable the mover after each reboot.
## Command
To do that automatically upon boot, simply add this: 
<br><br>
`sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"` 
<br><br>
to the end of your `/boot/config/go` to disable Unraid's mover.

---
At the end, your `/boot/config/go` should look like something like this:
```
#!/bin/bash

sed -i '/^start()/a echo "Mover disabled!" && exit 0' "$(which mover)"
```

### Why Disable Unraid's Mover Completely?
If you use ZFS, then Unraid's mover can get in the way of ZFS replication because the mover uses rsync. And personally, I have my own ZFS backup solution that replicates and snapshots from the `cache` pool to `array` pool.
Unraid's forum suggest disabling the mover **for a share** by setting its 'Second Storage' to none! No one wants to go through all of their `cache -> array` (or `cache <- array`) ZFS shares to `cache` (or `array`) just to prevent the mover from moving those shares. Also from my experience, ZFS's replication is way faster than rsync (plus you can have snapshots as a bonus).
 


