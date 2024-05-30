# syntax=docker/dockerfile:1
FROM caddy:2.8.0-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/cloudflare \
    --with github.com/WeidiDeng/caddy-cloudflare-ip

FROM caddy:2.8.0

COPY --from=builder /usr/bin/caddy /usr/bin/caddy