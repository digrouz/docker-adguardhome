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
        -v <path to config>:/opt/AdGuardHome/conf \
        -v <path to work>:/opt/AdGuardHome/work \
        -e GID=<GID default:12345> \
        -e AUTOUPGRADE=<0|1 default:0> \
        -e TZ=<timezone default:Europe/Brussels> \
        -p 53:53 \
        -p 67:67 \
        -p 68:68 \
        -p 80:80 \
        -p 443:443 \
        -p 853:853 \
        -p 3000:3000 \
        -p 5443:5443 \
        -p 6060:6060 \
    digrouz/adguardhome
        
## Environment Variables

When you start the `adguardhome` image, you can adjust the configuration of the `adguardhome` instance by passing one or more environment variables on the `docker run` command line.

### `GID`

This variable is not mandatory and specifies the group id that will be set to own configuration files of the application. It has default value `12345`.

### `AUTOUPGRADE`

This variable is not mandatory and specifies if the container has to launch software update at startup or not. Valid values are `0` and `1`. It has default value `0`.

### `TZ`

This variable is not mandatory and specifies the timezone to be configured within the container. It has default value `Europe/Brussels`.

## Notes

* This container is built using [s6-overlay](https://github.com/just-containers/s6-overlay)
* The docker entrypoint can upgrade operating system at each startup. To enable this feature, just add `-e AUTOUPGRADE=1` at container creation.
* Main process of this container is running as root, to allow to bind ports for DNS and DHCP.
* The port `53` is used for DNS (both TCP/UDP)
* The port `67` is used for DHCP server (UDP)
* The port `68` is used for DHCP client (UDP)
* The port `80` is used for HTTP (TCP)
* The port `443` is used for HTTPS, DNS-over-HTTPS, DNSCrypt (both TCP/UDP)
* The port `853` is used for DNS-over-TLS, DNS-over-QUIC (both TCP/UDP)
* The port `3000` is used for HTTPS (both TCP/UDP)
* The port `5443` is used for DNSCrypt (both TCP/UDP)
* The port `6060` is used for HTTP (TCP)

## Issues

If you encounter an issue please open a ticket at [github](https://github.com/digrouz/docker-adguardhome/issues)


