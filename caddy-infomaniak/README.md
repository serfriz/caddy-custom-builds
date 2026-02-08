# Caddy Docker build with Infomaniak DNS module

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--infomaniak%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-infomaniak)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--infomaniak%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-infomaniak)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--infomaniak%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-infomaniak)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-infomaniak.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-infomaniak.yml)

This image is updated automatically by GitHub Actions when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image and the following module:
- [**Infomaniak DNS**](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#dns-modules): for Infomaniak DNS-01 ACME validation support | [caddy-dns/infomaniak](https://github.com/caddy-dns/infomaniak)

## Usage

Since this image built off the official Caddy Docker image, the same [volumes](https://docs.docker.com/storage/volumes/) and/or [bind mounts](https://docs.docker.com/storage/bind-mounts/), ports mapping, etc. can be used with this container. Additional [environment variables](https://caddyserver.com/docs/caddyfile/concepts#environment-variables) may be needed for the added module. Please, refer to the repository's [README](https://github.com/serfriz/caddy-custom-builds?tab=readme-ov-file#container-creation) file for further usage instructions.

Docker builds for all Caddy supported platforms available at the following container registries:
- [**Docker Hub**](https://hub.docker.com/r/serfriz/caddy-infomaniak) `docker pull serfriz/caddy-infomaniak:latest`
- [**GitHub Packages**](https://ghcr.io/serfriz/caddy-infomaniak) `docker pull ghcr.io/serfriz/caddy-infomaniak:latest`
- [**Quay**](https://quay.io/serfriz/caddy-infomaniak) `docker pull quay.io/serfriz/caddy-infomaniak:latest`

### Tags

The following tags are available for the `serfriz/caddy-infomaniak` image:

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Contributing

Feel free to contribute, request additional Caddy images with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.
