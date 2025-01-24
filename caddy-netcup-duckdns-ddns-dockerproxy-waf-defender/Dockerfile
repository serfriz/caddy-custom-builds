# syntax=docker/dockerfile:1

# --- Stage 1: Builder Stage ---
# Use a Go base image to build the Caddy binary and the WAF module
FROM golang:latest AS builder

# Install essential tools for building: git, wget
#   - git: required for cloning the repository
#   - wget: required for downloading files
#   - &&: combines commands
#   - no-cache: prevents the apk installer from using the cache (smaller image)
RUN apk add --no-cache git wget

# Install xcaddy for building custom Caddy binaries with modules.
#   - @latest will install the latest available version.
RUN go install github.com/caddyserver/xcaddy/cmd/xcaddy@latest

# Set the working directory for the build process
WORKDIR /app

# Clone the caddy-waf repository from GitHub
RUN git clone https://github.com/fabriziosalmi/caddy-waf.git

# Change to the cloned directory
WORKDIR /app/caddy-waf

# Fetch and install the necessary Go dependencies, including Caddy and its modules and the caddy-waf plugin.
#  - go get will fetch and install all required modules
#  - go.mod will be used to properly build the project.
RUN go get -v github.com/caddyserver/caddy/v2 github.com/caddyserver/caddy/v2/caddyconfig/caddyfile github.com/caddyserver/caddy/v2/caddyconfig/httpcaddyfile github.com/caddyserver/caddy/v2 github.com/caddyserver/caddy/v2/modules/caddyhttp github.com/oschwald/maxminddb-golang github.com/fsnotify/fsnotify github.com/fabriziosalmi/caddy-waf

# Clean up and update the go.mod file
# - go mod tidy will tidy up go.mod file, removing unused dependencies
RUN go mod tidy

# Download the GeoLite2 Country database from a known location.
# - Use a reliable download location for this file.
RUN wget https://git.io/GeoLite2-Country.mmdb -O GeoLite2-Country.mmdb

# Clean up previous build artifacts, to ensure a clean build
RUN rm -rf buildenv_*

# Build the Caddy binary using xcaddy with the caddy-waf module.
#   - This creates the custom caddy binary with the waf

RUN xcaddy build \
    --with github.com/caddy-dns/netcup \
    --replace github.com/libdns/netcup=github.com/Monviech/libdns-netcup@libdns-patch \
    --with github.com/caddy-dns/duckdns \
    --with github.com/mholt/caddy-dynamicdns \
    --with github.com/lucaslorentz/caddy-docker-proxy/v2 \
    --with github.com/fabriziosalmi/caddy-waf=./ \
    --with github.com/jasonlovesdoggo/caddy-defender


FROM caddy:2.9.1

# Set the working directory for the running container.
WORKDIR /app

# Copy the Caddy binary from the builder stage.
#  - This copies the executable from the builder stage
COPY --from=builder /app/caddy-waf/caddy /usr/bin/caddy

# Copy the GeoLite2 database, rules, blacklists, and Caddyfile from the builder stage.
#  - This copies the files into the /app directory in the final image.
COPY --from=builder /app/caddy-waf/GeoLite2-Country.mmdb /app/
COPY --from=builder /app/caddy-waf/rules.json /app/
COPY --from=builder /app/caddy-waf/ip_blacklist.txt /app/
COPY --from=builder /app/caddy-waf/dns_blacklist.txt /app/
