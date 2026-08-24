- How to manage kernels 
```
# See what's installed
dpkg -l | grep pve-kernel

# See what GRUB offers
proxmox-boot-tool kernel list

# Remove an old kernel (and its headers)
apt remove pve-kernel-6.8.12-17-pve pve-headers-6.8.12-17-pve

# After removal, DKMS auto-cleans the module for that kernel
dkms status
```

- after a kernel update, always check:

```
uname -r
dpkg -l | grep "pve-kernel-$(uname -r | cut -d'-' -f1-2)"
```

- If the second command is empty, your running kernel isn't registered. Run:
```
apt install pve-kernel-$(uname -r)
```
to register it.

DKMS = Dynamic Kernel Module Support. When a kernel package installs, DKMS hooks fire and rebuild all out-of-tree modules (nvidia, zfs, virtualbox guest additions) for the new kernel. If headers aren't present, the build silently fails. Always check:
```
dkms status
# After every kernel update. If a module shows "installed" for your running kernel, you're good.
```
If it doesn't, force a rebuild:
```
dkms autoinstall
```

- check logs for container 
```
journalctl -u pve-container@200
# On the host
```

### freeze updates so after apt update it won't change 
```
apt-mark hold nvidia-smi libnvidia-ml1 libcuda1 libnvidia-cuda1
apt-mark showhold

# To unhold later:
apt-mark unhold libcuda1
```
usefull in LXC in Proxmox when nvidia drives must match on both systems: LXC and Proxmox

```
# Backup strategy: use vzdump (built-in)
# Daily incremental, weekly full, keep 7 daily + 4 weekly
# Config in /etc/vzdump.conf

# Monitor your host:
pvesh get /cluster/status
pvesh get /nodes/$(hostname)/memory
pvesh get /nodes/$(hostname)/disk

# Check LXC resource usage:
pvesh get /nodes/$(hostname)/lxc/200/status/current
```
- One-liner to check your whole GPU stack health
Run this after any apt upgrade or reboot. If any line is empty or wrong, you know exactly where the chain broke.
```
echo "=== Kernel ===" && uname -r && \
echo "=== DKMS ===" && dkms status && \
echo "=== Module loaded ===" && lsmod | grep nvidia && \
echo "=== nvidia-smi ===" && nvidia-smi --query-gpu=driver_version,name,memory.used --format=csv && \
echo "=== LXC devices ===" && ls /dev/nvidia*
```
