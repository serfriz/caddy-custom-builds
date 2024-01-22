# Caddy Docker build with Cloudflare dynamic DNS/IPs and Caddy Security modules

[![Docker Hub](https://img.shields.io/badge/Docker%20Hub%20-%20serfriz%2Fcaddy--cloudflare--ddns--security%20-%20%230db7ed?style=flat&logo=docker)](https://hub.docker.com/r/serfriz/caddy-cloudflare-ddns-security)
[![GitHub](https://img.shields.io/badge/GitHub%20-%20serfriz%2Fcaddy--cloudflare--ddns--security%20-%20%23333?style=flat&logo=github)](https://ghcr.io/serfriz/caddy-cloudflare-ddns-security)
[![Quay](https://img.shields.io/badge/Quay%20-%20serfriz%2Fcaddy--cloudflare--ddns--security%20-%20%23CC0000?style=flat&logo=redhat)](https://quay.io/serfriz/caddy-cloudflare-ddns-security)

[![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/serfriz/caddy-custom-builds?label=Release)](https://github.com/serfriz/caddy-custom-builds/releases)
[![GitHub build status](https://img.shields.io/github/actions/workflow/status/serfriz/caddy-custom-builds/build.caddy-cloudflare-ddns-security.yml?label=Build)](https://github.com/serfriz/caddy-custom-builds/actions/workflows/build.caddy-cloudflare-ddns-security.yml)
[![License](https://img.shields.io/github/license/serfriz/caddy-custom-builds?label=License)](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE)

This image is built automatically when a new version of [Caddy](https://github.com/caddyserver/caddy) is released using the official [Caddy Docker](https://hub.docker.com/_/caddy) image with the following modules:
- [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare) for Cloudflare DNS-01 ACME validation support.
- [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip) to retrieve Cloudflare's current [IP ranges](https://www.cloudflare.com/ips/).
- [mholt/caddy-dynamicdns](https://caddyserver.com/docs/modules/dynamic_dns) to update the DNS records with the public IP address of your instance.
- [greenpau/caddy-security](https://github.com/greenpau/caddy-security) for implementing different authentication methods (Form-Based, Basic, Local, LDAP, OpenID Connect, OAuth 2.0, SAML) including MFA/2FA support.

Docker builds for all supported platforms available at the following repositories:
- [Docker Hub](https://hub.docker.com/r/serfriz/caddy-cloudflare-ddns-security) `docker pull serfriz/caddy-cloudflare-ddns-security:latest`
- [GitHub Container Registry](https://ghcr.io/serfriz/caddy-cloudflare-ddns-security) `docker pull ghcr.io/serfriz/caddy-cloudflare-ddns-security:latest`
- [Quay Container Registry](https://quay.io/serfriz/caddy-cloudflare-ddns-security) `docker pull quay.io/serfriz/caddy-cloudflare-ddns-security:latest`

## Tags

The following tags are available for the `serfriz/caddy-cloudflare-ddns-security` image.

- `latest`
- `<version>` (eg: `2.7.4`, including: `2.7`, `2`, etc.)

## Usage

Since this is built off the official Docker image all of the same volumes, port mapping, environment variables, etc. can be used with this container. Please refer to the official [Caddy Docker](https://hub.docker.com/_/caddy) image and [docs](https://caddyserver.com/docs/) for more information on using Caddy.

### Create the Docker container

Simply create the container as usual including your `CLOUDFLARE_API_TOKEN` as [environment variable](https://caddyserver.com/docs/caddyfile/concepts#environment-variables).

```sh
docker run --rm -it \
  --name caddy \
  -p 80:80 \
  -p 443:443 \
  -v caddy-data:/data \
  -v caddy-config:/config \
  -v $PWD/Caddyfile:/etc/caddy/Caddyfile \
  -e CLOUDFLARE_API_TOKEN=UhKLc...JD9jk \
  serfriz/caddy-cloudflare-ddns-security:latest
```

### Cloudflare DNS-01 ACME validation

To make use of the Cloudflare DNS-01 ACME validation support at the server level, set the global [acme_dns](https://caddyserver.com/docs/caddyfile/options#acme-dns) directive in your `Caddyfile`.

```Caddyfile
{
  acme_dns cloudflare {env.CLOUDFLARE_API_TOKEN}
}
```

Or use the [`tls`](https://caddyserver.com/docs/caddyfile/directives/tls#tls) directive at each site. See the [caddy-dns/cloudflare](https://github.com/caddy-dns/cloudflare) module for additional details.

```Caddyfile
my.domain.tld {
  tls {
    dns cloudflare {env.CLOUDFLARE_API_TOKEN}
  }
}
```

#### Creating a Cloudflare API Token

You can generate a Cloudflare API token via the Cloudflare web dashboard through the following steps:

1. Login to your Cloudflare [Dashboard](https://dash.cloudflare.com/)
2. Go to [Account Profile](https://dash.cloudflare.com/profile) > [API Tokens](https://dash.cloudflare.com/profile/api-tokens)
3. Click "Create token" (Use the "Create Custom Token" option)
4. Grant the following permissions:
   - `Zone > Zone > Read`
   - `Zone > DNS > Edit`

### Cloudflare IP ranges

To restrict access to your server only to Cloudflare's IP ranges, add the [trusted_proxies](https://caddyserver.com/docs/caddyfile/options#trusted-proxies) directive to the [global options](https://caddyserver.com/docs/caddyfile/options), under servers, in your `Caddyfile`. For additional details, refer to [trusted_proxies/cloudflare](https://caddyserver.com/docs/json/apps/http/servers/trusted_proxies/cloudflare/) documentation and [WeidiDeng/caddy-cloudflare-ip](https://github.com/WeidiDeng/caddy-cloudflare-ip) repository.

```Caddyfile
{
  servers {
    trusted_proxies cloudflare {
      interval 12h
      timeout 15s
    }
  }
}
```

### Dynamic DNS

To keep your Cloudflare DNS records updated with the public IP address of your instance, add the [dynamic_dns](https://caddyserver.com/docs/modules/dynamic_dns) directive to the [global options](https://caddyserver.com/docs/caddyfile/options) in your `Caddyfile`. This module regularly queries a service for your public IP address and updates the DNS records via Cloudflare's API whenever it changes. For additional details and advanced configuration examples refer to [mholt/caddy-dynamicdns](https://github.com/mholt/caddy-dynamicdns) repository.

```Caddyfile
{
	dynamic_dns {
		provider cloudflare {env.CLOUDFLARE_API_TOKEN}
		domains {
			domain.tld
		}
	}
}
```

Using the option [dynamic_domains](https://github.com/mholt/caddy-dynamicdns#dynamic-domains), it can also be configured to scan through the domains configured in the Caddyfile and try to manage those DNS records.

### Caddy Security

Please, refer to the official [greenpau/caddy-security](https://authp.github.io/) documentation for additional details and configuration examples.

## Contributing

Feel free to contribute, request additional Caddy custom builds with your preferred modules, and make things better by opening an [Issue](https://github.com/serfriz/caddy-custom-builds/issues) or [Pull Request](https://github.com/serfriz/caddy-custom-builds/pulls).

## License

Software under [GPL-3.0](https://github.com/serfriz/caddy-custom-builds/blob/main/LICENSE) ensures users' freedom to use, modify, and distribute it while keeping the source code accessible. It promotes transparency, collaboration, and knowledge sharing. Users agree to comply with the GPL-3.0 license terms and provide the same freedom to others.