# syntax=docker/dockerfile:1
FROM caddy:2.7.5-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/duckdns \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http

FROM caddy:2.7.5

COPY --from=builder /usr/bin/caddy /usr/bin/caddy