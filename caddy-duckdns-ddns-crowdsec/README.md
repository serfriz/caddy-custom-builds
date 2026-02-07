# Caddy Docker build with DuckDNS Dynamic DNS and CrowdSec Bouncer modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--duckdns--ddns--crowdsec%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-duckdns-ddns-crowdsec)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--duckdns--ddns--crowdsec%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-duckdns-ddns-crowdsec)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--duckdns--ddns--crowdsec%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-duckdns-ddns-crowdsec)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-duckdns-ddns-crowdsec.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-duckdns-ddns-crowdsec.yml)

This image is updated automatically by GitHub Actions when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image and the following modules:
- [**DuckDNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dns-modules): for DuckDNS DNS-01 ACME validation support | [caddy-dns/duckdns](https://github.com/caddy-dns/duckdns)
- [**Dynamic DNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dynamic-dns): updates the DNS records with the public IP address of your instance | [mholt/caddy-dynamicdns](https://caddyserver.com/docs/modules/dynamic_dns)
- [**CrowdSec Bouncer**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#crowdsec-bouncer): to blocks malicious traffic based on [CrowdSec](https://www.crowdsec.net/) decisions | [hslatman/caddy-crowdsec-bouncer](https://github.com/hslatman/caddy-crowdsec-bouncer)

## Usage

Since this image built off the official Caddy Docker image, the same [volumes](https://docs.docker.com/storage/volumes/) and/or [bind mounts](https://docs.docker.com/storage/bind-mounts/), ports mapping, etc. can be used with this container. Additional [environment variables](https://caddyserver.com/docs/caddyfile/concepts#environment-variables) may be needed for the added modules. Please, refer to the repository's [README](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#container-creation) file for further usage instructions.

Docker builds for all Caddy supported platforms available at the following container registries:
- [**Docker Hub**](https://hub.docker.com/r/serfriz/caddy-duckdns-ddns-crowdsec) `docker pull serfriz/caddy-duckdns-ddns-crowdsec:latest`
- [**GitHub Packages**](https://ghcr.io/serfriz/caddy-duckdns-ddns-crowdsec) `docker pull ghcr.io/serfriz/caddy-duckdns-ddns-crowdsec:latest`
- [**Quay**](https://quay.io/serfriz/caddy-duckdns-ddns-crowdsec) `docker pull quay.io/serfriz/caddy-duckdns-ddns-crowdsec:latest`

### Tags

The following tags are available for the `serfriz/caddy-duckdns-ddns-crowdsec` image:

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Contributing

Feel free to contribute, request additional Caddy images with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.
