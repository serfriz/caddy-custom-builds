# syntax=docker/dockerfile:1
FROM caddy:2.8.4-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/WeidiDeng/caddy-cloudflare-ip \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http

FROM caddy:2.8.4

COPY --from=builder /usr/bin/caddy /usr/bin/caddy