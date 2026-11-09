# syntax=docker/dockerfile:1
FROM caddy:2.11.9-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/porkbun \
    --with github.com/porech/caddy-maxmind-geolocation \
    --with github.com/mholt/caddy-ratelimit

FROM caddy:2.11.9

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
