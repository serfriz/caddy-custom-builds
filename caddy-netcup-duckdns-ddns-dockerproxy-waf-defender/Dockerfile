# syntax=docker/dockerfile:1
FROM caddy:2.9.1-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/netcup \
    --replace github.com/libdns/netcup=github.com/Monviech/libdns-netcup@libdns-patch \
    --with github.com/caddy-dns/duckdns \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/lucaslorentz/caddy-docker-proxy/v2 \
    --with github.com/fabriziosalmi/caddy-waf \
    --with github.com/jasonlovesdoggo/caddy-defender

FROM caddy:2.9.1

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
