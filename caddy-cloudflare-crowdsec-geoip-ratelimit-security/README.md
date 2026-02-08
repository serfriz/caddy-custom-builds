# Caddy Docker build with Cloudflare DNS/IPs, CrowdSec Bouncer, GeoIP Filter, Rate Limit and Caddy Security modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--cloudflare--crowdsec--geoip--ratelimit--security%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--cloudflare--crowdsec--geoip--ratelimit--security%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--cloudflare--crowdsec--geoip--ratelimit--security%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-cloudflare-crowdsec-geoip-ratelimit-security.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-cloudflare-crowdsec-geoip-ratelimit-security.yml)

This image is updated automatically by GitHub Actions when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image and the following modules:
- [**Cloudflare DNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dns-modules): for Cloudflare DNS-01 ACME validation support | [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare)
- [**Cloudflare IPs**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#cloudflare-ips): to retrieve Cloudflare's current [IP ranges](https://www.cloudflare.com/ips/) | [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip)
- [**CrowdSec Bouncer**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#crowdsec-bouncer): blocks malicious traffic based on [CrowdSec](https://www.crowdsec.net/) decisions | [hslatman/caddy-crowdsec-bouncer](https://github.com/hslatman/caddy-crowdsec-bouncer)
- [**GeoIP Filter**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#geoip-filter): to allow or block traffic from specific regions based on [Maxmind GeoLite2 database](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data) | [porech/caddy-maxmind-geolocation](https://github.com/porech/caddy-maxmind-geolocation)
- [**Rate Limit**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#rate-limit): implements both internal and distributed HTTP rate limiting | [mholt/caddy-ratelimit](https://github.com/mholt/caddy-ratelimit)
- [**Caddy Security**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#caddy-security): to add different authentication methods including MFA/2FA support | [greenpau/caddy-security](https://github.com/greenpau/caddy-security)

## Usage

Since this image built off the official Caddy Docker image, the same [volumes](https://docs.docker.com/storage/volumes/) and/or [bind mounts](https://docs.docker.com/storage/bind-mounts/), ports mapping, etc. can be used with this container. Additional [environment variables](https://caddyserver.com/docs/caddyfile/concepts#environment-variables) may be needed for the added modules. Please, refer to the repository's [README](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#container-creation) file for further usage instructions.

Docker builds for all Caddy supported platforms available at the following container registries:
- [**Docker Hub**](https://hub.docker.com/r/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security) `docker pull serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security:latest`
- [**GitHub Packages**](https://ghcr.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security) `docker pull ghcr.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security:latest`
- [**Quay**](https://quay.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security) `docker pull quay.io/serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security:latest`

### Tags

The following tags are available for the `serfriz/caddy-cloudflare-crowdsec-geoip-ratelimit-security` image:

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Contributing

Feel free to contribute, request additional Caddy images with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.
