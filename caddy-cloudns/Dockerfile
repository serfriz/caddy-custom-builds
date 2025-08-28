# syntax=docker/dockerfile:1
FROM caddy:2.10.2-builder AS builder

RUN xcaddy build \
    --with github.com/anxuanzi/caddy-dns-ClouDNS

FROM caddy:2.10.2

COPY --from=builder /usr/bin/caddy /usr/bin/caddy