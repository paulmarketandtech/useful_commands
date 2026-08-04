1. Quick overall picture
```

df -h
```

Shows free/used space per filesystem. Note which mount points are full (usually / or /var).
```

df -ih          # inode usage (sometimes the problem is too many small files)
```

2. Find what’s eating spaceTop-level directories (on the root filesystem):
```
# start at root
du -xhd1 / 2>/dev/null | sort -hr

# -x stays on one filesystem, -d1 is depth 1.Drill into big ones (common culprits: /var, /home, /usr, /tmp, /opt):bash

du -xhd1 /var 2>/dev/null | sort -hr
du -xhd1 /home 2>/dev/null | sort -hr
# etc.
```

3. Large individual files:
```
find / -xdev -type f -size +100M -exec ls -lh {} \; 2>/dev/null | sort -k5 -hr

# Adjust +100M as needed. -xdev stays on one filesystem.
```

4. Safe cleaning steps
APT package cache & unused packages (very common and safe):

```

apt clean                    # removes downloaded .deb files
apt autoclean                # removes only obsolete ones
apt autoremove --purge       # removes packages that are no longer needed
```

### When your system is not fresh any more but mature enough to be considered legacy then you should definitely check this out.

Systemd journal (can grow large)
```

journalctl --disk-usage
journalctl --vacuum-size=200M  # last 200MB is more than you need
```

Or go to
```
/etc/systemd/journald.conf
```
and add/modify this line:
```
[Journal]
SystemMaxUse=100M
```

Or create a drop-in file. Do it manually or use this command:
```
sudo systemctl edit <service_name>
# in this case:
sudo systemctl edit systemd-journald

# add the SystemMaxUse line and restart the service
sudo systemctl restart systemd-journald

```
