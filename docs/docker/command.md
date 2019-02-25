# Docker Command

!!! note
    For documentation about writing images see: [Dockerfile examples and best practices](dockerfile.md)

## attach vs exec
When wanting to execute something inside a container, you can use either of `docker attach ...` or `docker exec -it ...` commands

The main difference between these two commands is that `attach` will kill PID 1 when you disconnect from your container.

The `exec` command do not kill PID 1, so your container will continue running

## Print all digest with full sha1
```bash
docker images --digests
```

## Print only ids
```bash
docker images ... -q
```

## Filter images
```bash
docker images --filter=reference='registry/*'
docker images --filter=reference='registry/*/*'
docker images --filter=reference='registry/*/*/*'
```

## Format output to get repository:tag
Available: .ID, .Repository, .Tag, .Digest, .CreatedSince, .CreatedAt, Size
```bash
docker images --filter=reference='registry/*/*/*' --format "{{.Repository}}:{{.Tag}}"
```

## Push all filtered images
```bash
for i in $(docker images --filter=reference='registry/*/*/*' --format "{{.Repository}}:{{.Tag}}"); do docker push $i; done
```

## Find containers folder name
```bash
sudo su -
for f in `find /var/lib/docker -name 'config.v2.json'`; do echo $f; cat $f | python -m json.tool | grep '"Name": "/r'; done | grep <application_name>
```
