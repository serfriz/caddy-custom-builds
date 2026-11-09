# syntax=docker/dockerfile:1
FROM caddy:2.11.9-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/dynu

FROM caddy:2.11.9

COPY --from=builder /usr/bin/caddy /usr/bin/caddy
