# syntax=docker/dockerfile:1
FROM docker.io/library/caddy:2.10.2-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/porkbun

FROM docker.io/library/caddy:2.10.2

COPY --from=builder /usr/bin/caddy /usr/bin/caddy