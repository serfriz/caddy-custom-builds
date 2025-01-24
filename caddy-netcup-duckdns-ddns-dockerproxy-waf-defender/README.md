# Caddy Docker build with Netcup, DuckDNS, Dynamic DNS, Docker Proxy and Defender modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--netcup--duckdns--ddns--dockerproxy--waf--defender%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-netcup-duckdns-ddns-dockerproxy-waf-defender)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--netcup--duckdns--ddns--dockerproxy--waf--defender%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-netcup-duckdns-ddns-dockerproxy-waf-defender)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--netcup--duckdns--ddns--dockerproxy--waf--defender%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-netcup-duckdns-ddns-dockerproxy-waf-defender)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-netcup-duckdns-ddns-dockerproxy-waf-defender.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-netcup-duckdns-ddns-dockerproxy-waf-defender.yml)

This image is updated automatically by GitHub Actions when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image and the following modules:
- [**Netcup DNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dns-modules): for Netcup DNS-01 ACME validation support | [caddy-dns/netcup](https://github.com/caddy-dns/netcup-ddns)
- [**DuckDNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dns-modules): for DuckDNS DNS-01 ACME validation support | [caddy-dns/duckdns](https://github.com/caddy-dns/duckdns)
- [**Dynamic DNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dynamic-dns): updates the DNS records with the public IP address of your instance | [mholt/caddy-dynamicdns](https://caddyserver.com/docs/modules/dynamic_dns)
- [**Docker Proxy**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#docker-proxy): enables Caddy to be used for Docker containers via labels | [lucaslorentz/caddy-docker-proxy](https://github.com/lucaslorentz/caddy-docker-proxy)
- [**Coraza WAF**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#coraza-waf): a Web Application Firewall (WAF) for Caddy | [corazawaf/coraza-caddy](https://github.com/corazawaf/coraza-caddy)
- [**Defender**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#defender): allows to block or manipulate requests based on the client's IP address | [JasonLovesDoggo/caddy-defender](https://github.com/JasonLovesDoggo/caddy-defender)

## Usage

Since this image built off the official Caddy Docker image, the same [volumes](https://docs.docker.com/storage/volumes/) and/or [bind mounts](https://docs.docker.com/storage/bind-mounts/), ports mapping, etc. can be used with this container. Additional [environment variables](https://caddyserver.com/docs/caddyfile/concepts#environment-variables) may be needed for the added modules. Please, refer to the repository's [README](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#container-creation) file for further usage instructions.

Docker builds for all Caddy supported platforms available at the following container registries:
- [**Docker Hub**](https://hub.docker.com/r/serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy) `docker pull serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy:latest`
- [**GitHub Packages**](https://ghcr.io/serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy) `docker pull ghcr.io/serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy:latest`
- [**Quay**](https://quay.io/serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy) `docker pull quay.io/serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy:latest`

### Tags

The following tags are available for the `serfriz/caddy-cloudflare-ddns-crowdsec-geoip-security-dockerproxy` image:

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Contributing

Feel free to contribute, request additional Caddy images with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.