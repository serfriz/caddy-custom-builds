# syntax=docker/dockerfile:1
FROM caddy:2.8.1-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/WeidiDeng/caddy-cloudflare-ip \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http \
    --with github.com/porech/caddy-maxmind-geolocation

FROM caddy:2.8.1

COPY --from=builder /usr/bin/caddy /usr/bin/caddy