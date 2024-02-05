# Caddy Docker build with Rate Limit, Docker Proxy and Sablier modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--ratelimit--dockerproxy--sablier%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-ratelimit-dockerproxy-sablier)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--ratelimit--dockerproxy--sablier%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-ratelimit-dockerproxy-sablier)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--ratelimit--dockerproxy--sablier%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-ratelimit-dockerproxy-sablier)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-ratelimit-dockerproxy-sablier.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-ratelimit-dockerproxy-sablier.yml)
[![License](https://img.shields.io/github/license/serfriz/caddy-custom-builds?label=License)](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE)

This image is built automatically when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image with the following modules:
- [mholt/caddy-ratelimit](https://github.com/mholt/caddy-ratelimit) implements both internal and distributed HTTP rate limiting. Requests can be rejected after a specified rate limit is hit.
- [lucaslorentz/caddy-docker-proxy](https://github.com/lucaslorentz/caddy-docker-proxy) enables Caddy to be used as a reverse proxy for Docker containers via labels.
- [acouvreur/sablier](https://github.com/acouvreur/sablier) to start your containers on demand and shut them down automatically after a period of inactivity.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-ratelimit-dockerproxy-sablier) `docker pull serfriz/caddy-ratelimit-dockerproxy-sablier:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-ratelimit-dockerproxy-sablier) `docker pull ghcr.io/serfriz/caddy-ratelimit-dockerproxy-sablier:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-ratelimit-dockerproxy-sablier) `docker pull quay.io/serfriz/caddy-ratelimit-dockerproxy-sablier:latest`

## Tags

The following tags are available for the `serfriz/caddy-ratelimit-dockerproxy-sablier` image.

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Usage

Since this is built off the official Docker image all of the same volumes, port mapping, environment variables, etc. can be used with this container. Please refer to the official [Caddy Docker](https://hub.docker.com/_/caddy) image and [docs](https://caddyserver.com/docs/) for more information on using Caddy.

### Create the Docker container

Simply create the container as usual.

```sh
docker run --rm -it \
  --name caddy \
  -p 80:80 \
  -p 443:443 \
  -v caddy-data:/data \
  -v caddy-config:/config \
  -v $PWD/Caddyfile:/etc/caddy/Caddyfile \
  serfriz/caddy-ratelimit-dockerproxy-sablier:latest
```

### Rate Limit

The [rate_limit](https://caddyserver.com/docs/modules/http.handlers.rate_limit#github.com/mholt/caddy-ratelimit) HTTP handler module lets you define rate limit zones, which have a unique name of your choosing. If a rate limit is exceeded, an HTTP error with status 429 will be returned. This error can be handled using the conventional error handling routes in your config.

Additional information and Caddyfile configuration examples can be found in the [mholt/caddy-ratelimit](https://github.com/mholt/caddy-ratelimit) repository.

### Docker Proxy

The plugin scans Docker metadata, looking for labels indicating that the service or container should be served by Caddy. Then, it generates an in-memory Caddyfile with site entries and proxies pointing to each Docker service by their DNS name or container IP. Every time a Docker object changes, the plugin updates the Caddyfile and triggers Caddy to gracefully reload, with zero-downtime.

Additional information and Caddyfile configuration examples can be found in the [lucaslorentz/caddy-docker-proxy](https://github.com/lucaslorentz/caddy-docker-proxy) repository.

### Sablier

[Sablier](https://github.com/acouvreur/sablier) is a free and open-source software that can scale your workloads on demand following different strategies. Your workloads can be a docker container, a kubernetes deployment and more (see [providers](https://acouvreur.github.io/sablier/#/providers/overview) for the full list). This plugin provides an integration with Caddy.

Additional information and Caddyfile configuration examples can be found in the [acouvreur/sablier](https://acouvreur.github.io/sablier/#/plugins/caddy) documentation.

## Contributing

Feel free to contribute, request additional Caddy custom builds with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.