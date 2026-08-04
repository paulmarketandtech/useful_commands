### Basic commands for browsing journalctl

```

# How big is it right now?
journalctl --disk-usage

# Last boot only
journalctl -b

# Previous boot
journalctl -b -1

# Last N lines (like tail)
journalctl -n 200

# Follow live (like tail -f)
journalctl -f

# Only errors and worse
journalctl -p err..alert

# Time range
journalctl --since "2026-07-01" --until "2026-07-15"
journalctl --since "1 week ago"
journalctl --since today

# Specific service / unit
journalctl -u ssh.service
journalctl -u nginx

# Search for a string (case-insensitive)
journalctl -g "error|fail|warn" --no-pager

# Pipe to less so you can scroll / search
journalctl -b | less
# inside less: /pattern to search, n for next, q to quit
```

