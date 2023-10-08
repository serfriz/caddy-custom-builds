# Caddy Docker Custom Builds
[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/update-tag-release.yml?label=Auto-update)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/update-tag-release.yml)
[![License](https://img.shields.io/github/license/serfriz/caddy-custom-builds?label=License)](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE)

This repository aims to provide flexibility and convenience to run [Caddy](https://github.com/caddyserver/caddy) with specific combinations of modules according to users' needs and preferences. All images are built automatically when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image.

If you are looking for a specific custom build not available yet in this repository, please create a new [Issue](https://github.com/serfriz/caddy-custom-builds/issues) with your request. 

## Build with Cloudflare DNS and IP modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--cloudflare%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-cloudflare)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--cloudflare%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-cloudflare)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--cloudflare%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-cloudflare)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-cloudflare.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-cloudflare.yml)

Caddy Docker custom build with the following modules:
- [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare) for Cloudflare DNS-01 ACME validation support.
- [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip) to retrieve Cloudflare's current [IP ranges](https://www.cloudflare.com/ips/).

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-cloudflare) `docker pull serfriz/caddy-cloudflare:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-cloudflare) `docker pull ghcr.io/serfriz/caddy-cloudflare:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-cloudflare) `docker pull quay.io/serfriz/caddy-cloudflare:latest`

Additional details and usage instructions available in the build's [README](https://github.com/serfriz/caddy-custom-builds/tree/main/caddy-cloudflare) file.

## Build with Cloudflare dynamic DNS and IP modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--cloudflare--ddns%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-cloudflare-ddns)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--cloudflare--ddns%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-cloudflare-ddns)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--cloudflare--ddns%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-cloudflare-ddns)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-cloudflare-ddns.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-cloudflare-ddns.yml)

Caddy Docker custom build with the following modules:
- [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare) for Cloudflare DNS-01 ACME validation support.
- [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip) to retrieve Cloudflare's current [IP ranges](https://www.cloudflare.com/ips/).
- [mholt/caddy-dynamicdns](https://caddyserver.com/docs/modules/dynamic_dns) to update the DNS records with the public IP address of your instance.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-cloudflare-ddns) `docker pull serfriz/caddy-cloudflare-ddns:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-cloudflare-ddns) `docker pull ghcr.io/serfriz/caddy-cloudflare-ddns:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-cloudflare-ddns) `docker pull quay.io/serfriz/caddy-cloudflare-ddns:latest`

Additional details and usage instructions available in the build's [README](https://github.com/serfriz/caddy-custom-builds/tree/main/caddy-cloudflare-ddns) file.

## Build with Cloudflare DNS/IP and CrowdSec Bouncer modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--cloudflare--crowdsec%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-cloudflare-crowdsec)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--cloudflare--crowdsec%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-cloudflare-crowdsec)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--cloudflare--crowdsec%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-cloudflare-crowdsec)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-cloudflare-crowdsec.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-cloudflare-crowdsec.yml)

Caddy Docker custom build with the following modules:
- [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare) for Cloudflare DNS-01 ACME validation support.
- [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip) to retrieve Cloudflare's current [IP ranges](https://www.cloudflare.com/ips/).
- [hslatman/caddy-crowdsec-bouncer](https://github.com/hslatman/caddy-crowdsec-bouncer) to block malicious traffic based on [CrowdSec](https://www.crowdsec.net/) decisions.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-cloudflare-crowdsec) `docker pull serfriz/caddy-cloudflare-crowdsec:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-cloudflare-crowdsec) `docker pull ghcr.io/serfriz/caddy-cloudflare-crowdsec:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-cloudflare-crowdsec) `docker pull quay.io/serfriz/caddy-cloudflare-crowdsec:latest`

Additional details and usage instructions available in the build's [README](https://github.com/serfriz/caddy-custom-builds/tree/main/caddy-cloudflare-crowdsec) file.

## Build with CrowdSec Bouncer module

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--crowdsec%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-crowdsec)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--crowdsec%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-crowdsec)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--crowdsec%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-crowdsec)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-crowdsec.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-crowdsec.yml)

Caddy Docker custom build with the following module:
- [hslatman/caddy-crowdsec-bouncer](https://github.com/hslatman/caddy-crowdsec-bouncer) to block malicious traffic based on [CrowdSec](https://www.crowdsec.net/) decisions.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-crowdsec) `docker pull serfriz/caddy-crowdsec:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-crowdsec) `docker pull ghcr.io/serfriz/caddy-crowdsec:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-crowdsec) `docker pull quay.io/serfriz/caddy-crowdsec:latest`

Additional details and usage instructions available in the build's [README](https://github.com/serfriz/caddy-custom-builds/tree/main/caddy-crowdsec) file.

## Contributing

Feel free to contribute, request additional Caddy custom builds with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.