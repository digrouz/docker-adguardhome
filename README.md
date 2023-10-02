[![auto-update](https://github.com/digrouz/docker-adguardhome/actions/workflows/auto-update.yml/badge.svg)](https://github.com/digrouz/docker-adguardhome/actions/workflows/auto-update.yml)
[![dockerhub](https://github.com/digrouz/docker-adguardhome/actions/workflows/dockerhub.yml/badge.svg)](https://github.com/digrouz/docker-adguardhome/actions/workflows/dockerhub.yml)
![Docker Pulls](https://img.shields.io/docker/pulls/digrouz/adguardhome)

# docker-adguardhome

Install adguardhome into a Linux container

![adguardhome](https://github.com/AdguardTeam/AdGuardHome/raw/master/doc/adguard_home_lightmode.svg)

## Tag
Several tag are available:
* latest: see alpine
* alpine: [Dockerfile_alpine](https://github.com/digrouz/docker-adguardhome/blob/master/Dockerfile_alpine)
* Any version specific tag is based on alpine.

## Description
AdGuard Home is a network-wide software for blocking ads and tracking. After you set it up, it'll cover ALL your home devices, and you don't need any client-side software for that.

It operates as a DNS server that re-routes tracking domains to a “black hole”, thus preventing your devices from connecting to those servers. It's based on software we use for our public AdGuard DNS servers, and both share a lot of code.

https://adguard.com/

## Usage
    docker create --name=adguardhome \
        -v <path to data>:/config \
        -e UID=<UID default:12345> \
        -e GID=<GID default:12345> \
        -e AUTOUPGRADE=<0|1 default:0> \
        -e TZ=<timezone default:Europe/Brussels> \
        -p 8080:8080 \
    digrouz/adguardhome
        
## Environment Variables

When you start the `adguardhome` image, you can adjust the configuration of the `adguardhome` instance by passing one or more environment variables on the `docker run` command line.

### `UID`

This variable is not mandatory and specifies the user id that will be set to run the application. It has default value `12345`.

### `GID`

This variable is not mandatory and specifies the group id that will be set to run the application. It has default value `12345`.

### `AUTOUPGRADE`

This variable is not mandatory and specifies if the container has to launch software update at startup or not. Valid values are `0` and `1`. It has default value `0`.

### `TZ`

This variable is not mandatory and specifies the timezone to be configured within the container. It has default value `Europe/Brussels`.

## Notes

* This container is built using [s6-overlay](https://github.com/just-containers/s6-overlay)
* The docker entrypoint can upgrade operating system at each startup. To enable this feature, just add `-e AUTOUPGRADE=1` at container creation.

## Issues

If you encounter an issue please open a ticket at [github](https://github.com/digrouz/docker-adguardhome/issues)


