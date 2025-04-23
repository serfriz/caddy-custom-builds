# syntax=docker/dockerfile:1
FROM caddy:2.10.0-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/netlify \
    --with github.com/porech/caddy-maxmind-geolocation \
    --with github.com/greenpau/caddy-security

FROM caddy:2.10.0

COPY --from=builder /usr/bin/caddy /usr/bin/caddy