rancher-traefik
==============

This image is the traefik dynamic conf for rancher. It comes from [rawmind/rancher-tools][rancher-tools].

## Build

```
docker build -t rawmind/rancher-traefik:<version> .
```

## Versions

- `0.0.1` [(Dockerfile)](https://github.com/rawmind0/rancher-traefik/blob/master/Dockerfile)


## Usage

This image has to be run as a sidekick of [rawmind/alpine-traefik][alpine-traefik], and makes available /opt/tools volume. It scans from rancher-metadata, for a services that has traefik labels, and generates traefik frontend and backends to expose the services.


## Configuration labels

Traefik labels, has to be created in your service, in order to get included in traefik dynamic config.

- traefik.enable = *true | stack | false* #Controls if you want to publish or not the service
  - true: the service will be published as *service_name.stack_name.traefik_domain*
  - stack: the service will be published as *stack_name.domain*. WARNING: You can have collisions inside services within yout stack
  - false: the service will not be published
- traefik.domain	= *Domain name to route rule*
- traefik.port = *port to expose throught traefik*

[alpine-traefik]: https://github.com/rawmind0/alpine-traefik
[rancher-tools]: https://github.com/rawmind0/rancher-tools
