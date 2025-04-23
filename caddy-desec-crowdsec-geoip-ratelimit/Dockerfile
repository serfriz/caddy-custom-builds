# syntax=docker/dockerfile:1
FROM caddy:2.10.0-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/desec \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http \
    --with github.com/porech/caddy-maxmind-geolocation \
    --with github.com/mholt/caddy-ratelimit

FROM caddy:2.10.0

COPY --from=builder /usr/bin/caddy /usr/bin/caddy