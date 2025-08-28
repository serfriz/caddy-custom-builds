# syntax=docker/dockerfile:1
FROM caddy:2.10.2-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/duckdns \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http \
    --with github.com/porech/caddy-maxmind-geolocation \
    --with github.com/greenpau/caddy-security \
    --with github.com/lucaslorentz/caddy-docker-proxy/v2

FROM caddy:2.10.2

COPY --from=builder /usr/bin/caddy /usr/bin/caddy

CMD ["caddy", "docker-proxy"]