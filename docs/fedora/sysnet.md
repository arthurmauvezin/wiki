# Fedora: System & Network

## Disable IPv6
```bash
sudo su -
sysctl -w net.ipv6.conf.all.disable_ipv6=1
sysctl -w net.ipv6.conf.default.disable_ipv6=1
```

## Delete old kernels
### Check installed kernels
```bash
rpm -q kernel
```

### Delete old kernels (count = number of kernel wanted to left)
```bash
dnf install yum-utils
package-cleanup --oldkernels --count=2
```

### Make these changes permanent
Edit /etc/yum.conf or /etc/dnf/dnf.conf and set installonly_limit:
```bash
installonly_limit=2
```
