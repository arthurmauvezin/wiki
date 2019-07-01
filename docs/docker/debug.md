# Debug

## Analyse container swap

```bash
for container in $(docker ps --format "{{.Names}}");
do
        echo $container;
        cat /proc/$(docker inspect $container --format "{{.State.Pid}}")/status | grep -E "VmSize|VmSwap";
done
```
