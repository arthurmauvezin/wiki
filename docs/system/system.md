# System useful commands

## Memory usage

### Get state of memory
```bash
free -m
```

### Free swap
```bash
echo 1 > /proc/sys/vm/drop_caches
swap off -a
echo 1 > /proc/sys/vm/drop_caches
```
