# Docker templates

## Dockerfile: [ALPINE] Secured image
```Dockerfile
FROM <baseimage>

#REPOSITORIES=<repo>
#TAGS=<tag>

# Copy pip config and entrypoint
COPY entrypoint.sh /

# Setup date and runtime user encapsulation
RUN apk add --no-cache tzdata tini su-exec \
 && cp /usr/share/zoneinfo/Europe/Paris /etc/localtime \
 && addgroup -g 1000 -S <group_name> \
 && adduser -u 1000 -S <user_name> -G <group_name> \
 && chmod +x /entrypoint.sh

# Encapsulate execution through tini and python user
ENTRYPOINT ["/sbin/tini", "--", "/entrypoint.sh"]
CMD ["<command>"]
```

## Entrypoint: [ALPINE] Running with user
```bash
#!/bin/sh

set -euo pipefail

exec su-exec <user_name>:<group_name> "$@"
```

## Entrypoint: Allow interactive (withour --entrypoint)
```bash
if [ $# -eq 1 ]; then
        # if `docker run` only has one arguments, we assume user is running alternate command like `bash` or `sh` to inspect the image
        exec "$@"
else
```
