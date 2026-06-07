# syntax=docker/dockerfile:1
FROM caddy:2.11.4-builder AS builder

RUN xcaddy build \
    --with github.com/hslatman/caddy-crowdsec-bouncer/http \
    --with github.com/hslatman/caddy-crowdsec-bouncer/appsec

FROM caddy:2.11.4

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
