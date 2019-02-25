# Dockerfile Best Practice

## Build, Tag and push shortcut
This it not a standard command but a custom one. This is an open source command line tool [you can get here](https://github.com/arthurmauvezin/docker-embark).
Simply add the following comments to your docker file
```bash
#REPOSITORIES=regitry/repository_name
#TAGS=version
```
And execute
```bash
docker-embark . 
```
Or:
```bash
docker-embark path/to/Dockerfile
```

## Download and extraxt archives with wget (prefer this method as wget is already installed on alpine images)
```Dockerfile
RUN wget http://example.com/archive.tar.gz -O - | tar -xz(j) [--strip-components={N}] [--directory=/my/directory/]
```

## Download and extraxt archives with curl
```Dockerfile
RUN curl http://example.com/archive.tar.gz | tar -xz(j) [--strip-components={N}] [--directory=/my/directory/]
```

## Set time inside container
Alpine:
```Dockerfile
RUN apk add --no-cache tzdata
ENV TZ=Europe/Paris
```

Debian:
```Dockerfile
RUN TZ="Europe/Paris" \
 && ln -snf /usr/share/zoneinfo/$TZ /etc/localtime \
 && echo $TZ > /etc/timezone
```

## Create user and group
Alpine:
```Dockerfile
RUN addgroup -g 1000 -S <group_name> \
 && adduser -u 1000 -S <user_name> -G <group_name>
```

Debian:
```Dockerfile
RUN groupadd -g 1000 -r python \
 && useradd --no-log-init -u 1000 -r -g python python
```

## Install package properly
Alpine:
```Dockerfile
RUN apk add --no-cache <package_list>
```

Debian:
```Dockerfile
RUN apt-get -y -q update --no-install-recommends \
 && apt-get -y -q install --no-install-recommends <package_list> \
 && apt-get clean autoclean \
 && apt-get autoremove --yes \
 && rm -rf /var/lib/{apt,dpkg,cache,log}/
```

## Work with build dependencies
Sometimes you need to install build time only dependencies which are not needed to run your app. In these case, use the solution hereafter to save some space.

Alpine:
```Dockerfile
RUN apk add --no-cache --virtual build-dependencies <dependencies_package_list> \
 && echo "... INSTALL STUFF HERE ..." \
 && apk del build-depencies
```

Debian:
```Dockerfile
RUN apt-get -y -q update --no-install-recommends \
 && apt-get -y -q install --no-install-recommends <dependencies_package_list> \
 && apt get -y purge <dependencies_package_list> \
 && apt-get clean autoclean \
 && apt-get autoremove --yes \
 && rm -rf /var/lib/{apt,dpkg,cache,log}/
```

## Install Docker client
Alpine:
```Dockerfile
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories \
 && apk add --no-cache docker
```

Debian:
```Dockerfile
RUN apt-get -y -q update --no-install-recommends \
 && apt-get -y -q install --no-install-recommends \
     apt-transport-https \
     ca-certificates \
     curl \
     gnupg2 \
     software-properties-common \
 && curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add - \
 && add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/debian \
      $(lsb_release -cs) \
      stable" \
 && apt-get -y -q update --no-install-recommends \
 && apt-get -y -q install --no-install-recommends docker-ce \
 && apt-get clean autoclean \
 && apt-get autoremove --yes \
 && rm -rf /var/lib/{apt,dpkg,cache,log}/
```

## Install Glibc
!!! warning
    Alpine's glibc version is not working with every software. I encountered some problems on couchbase or    oracle binaries.

Alpine:
```Dockerfile
RUN apk --no-cache add ca-certificates \
 && wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://raw.githubusercontent.com/sgerrand/alpine-pkg-glibc/master/sgerrand.rsa.pub \
 && wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.25-r0/glibc-2.25-r0.apk \
 && apk add glibc-2.25-r0.apk \
 && rm -rf glibc-2.25-r0.apk 
```

## Add entrypoint file
```bash
COPY docker-entrypoint.sh /
RUN chmod +x entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
CMD ["<default_command_to_entrypoint_script>"]
```

## Setup Tini
Alpine:
```Dockerfile
RUN apk add --no-cache tini

ENTRYPOINT ["/sbin/tini", "--", "<command>"]
```

Debian:
```Dockerfile
RUN apt-get -y -q update --no-install-recommends \
 && apt-get -y -q install --no-install-recommends curl \
 && TINI_VERSION="v0.18.0" \
 && curl -L https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini -o /tini \
 && chmod +x /tini \
 && apt-get -y purge curl \
 && apt-get clean autoclean \
 && apt-get autoremove --yes \
 && rm -rf /var/lib/{apt,dpkg,cache,log}/ \

ENTRYPOINT ["/tini", "--", "<command>"]
```

## Env var in ENTRYPOINT
```bash
ENTRYPOINT ["/bin/sh", "-c", "echo $MY_ENV"]
```

