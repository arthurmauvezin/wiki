# Docker Compose

## Start compose interactively
```yaml
version: '3'
services:
  service-name:
    image: image-name
    stdin_open: true
    tty: true
    command:
      - 'sh'
```
