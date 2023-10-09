# Caddy Docker build with DuckDNS DNS module

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--duckdns%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-duckdns)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--duckdns%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-duckdns)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--duckdns%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-duckdns)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-duckdns.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-duckdns.yml)
[![License](https://img.shields.io/github/license/serfriz/caddy-custom-builds?label=License)](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE)

This image is built automatically when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image with the following modules:
- [caddy-dns/duckdns](https://github.com/caddy-dns/duckdns) for DuckDNS DNS-01 ACME validation support.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-duckdns) `docker pull serfriz/caddy-duckdns:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-duckdns) `docker pull ghcr.io/serfriz/caddy-duckdns:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-duckdns) `docker pull quay.io/serfriz/caddy-duckdns:latest`

## Tags

The following tags are available for the `serfriz/caddy-duckdns` image.

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Usage

Since this is built off the official Docker image all of the same volumes, port mapping, environment variables, etc. can be used with this container. Please refer to the official [Caddy Docker](https://hub.docker.com/_/caddy) image and [docs](https://caddyserver.com/docs/) for more information on using Caddy.

### Create the Docker container

Simply create the container as usual including your `DUCKDNS_API_TOKEN` as [environment variable](https://caddyserver.com/docs/caddyfile/concepts#environment-variables).

```sh
docker run --rm -it \
  --name caddy \
  -p 80:80 \
  -p 443:443 \
  -v caddy-data:/data \
  -v caddy-config:/config \
  -v $PWD/Caddyfile:/etc/caddy/Caddyfile \
  -e DUCKDNS_API_TOKEN=UhKLc...JD9jk \
  serfriz/caddy-duckdns:latest
```

### DuckDNS DNS-01 ACME validation

To make use of the DuckDNS DNS-01 ACME validation support at the server level, set the global [acme_dns](https://caddyserver.com/docs/caddyfile/options#acme-dns) directive in your `Caddyfile`.

```Caddyfile
{
  acme_dns duckdns {env.DUCKDNS_API_TOKEN}
}
```

Or use the [`tls`](https://caddyserver.com/docs/caddyfile/directives/tls#tls) directive at each site. See the [caddy-dns/duckdns](https://github.com/caddy-dns/duckdns) module for additional details.

```Caddyfile
my.domain.tld {
  tls {
    dns duckdns {env.DUCKDNS_API_TOKEN}
  }
}
```

#### Creating a DuckDNS API Token

To generate a DuckDNS API token, go to the DuckDNS website and click in the header's three small lines, next to your logged in email, then click on the recreate token button. Copy the token and use it as the `DUCKDNS_API_TOKEN` environment variable.

## Contributing

Feel free to contribute, request additional Caddy custom builds with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.