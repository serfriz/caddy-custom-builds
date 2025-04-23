# syntax=docker/dockerfile:1
FROM caddy:2.10.0-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/netcup \
    --with github.com/mholt/caddy-dynamicdns \
    --replace github.com/libdns/netcup=github.com/Monviech/libdns-netcup@libdns-patch

FROM caddy:2.10.0

COPY --from=builder /usr/bin/caddy /usr/bin/caddy