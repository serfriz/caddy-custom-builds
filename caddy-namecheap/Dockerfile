# syntax=docker/dockerfile:1
FROM caddy:2.9.1-builder AS builder

RUN xcaddy build \
    --with github.com/caddy-dns/namecheap

FROM caddy:2.9.1

COPY --from=builder /usr/bin/caddy /usr/bin/caddy