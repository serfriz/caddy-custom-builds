# syntax=docker/dockerfile:1
FROM caddy:2.11.2-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/bunny \
    --with github.com/mholt/caddy-dynamicdns

FROM caddy:2.11.2

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
