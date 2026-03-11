# syntax=docker/dockerfile:1
FROM caddy:2.11.2-builder AS builder

RUN xcaddy build \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http \
    --with github.com/hslatman/caddy-crowdsec-bouncer/appsec \
    --with github.com/porech/caddy-maxmind-geolocation

FROM caddy:2.11.2

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
