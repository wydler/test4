# ----------------------------------------
# Stage 1: Build / Download MediathekView
# ----------------------------------------
FROM debian:13.4-slim@sha256:4ffb3a1511099754cddc70eb1b12e50ffdb67619aa0ab6c13fcd800a78ef7c7a AS builder

# ----------------------------------------
# Build-Argument
# ----------------------------------------
ARG TARGETARCH

# Setze Arbeitsverzeichnis für temporäre Dateien
WORKDIR /tmp

# ----------------------------------------
# Kopiere nur die mediathekview.version
# Diese enthält die gewünschte MediathekView-Version
# ----------------------------------------
COPY mediathekview.version /tmp/mediathekview.version

# ----------------------------------------
# Installiere wget und ca-certificates für HTTPS-Download
# --no-install-recommends hält das Image klein
# ----------------------------------------
RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    wget \
    ca-certificates \
 && rm -rf /var/lib/apt/lists/*

# ----------------------------------------
# Create /opt/MediathekView directory and download the correct MediathekView archive
# based on the build target architecture (TARGETARCH).  
# - For arm64 builds, use "linux-aarch64" archive  
# - For amd64 builds, use "linux" archive  
# Then extract the archive to /opt and clean up temporary files.
# ----------------------------------------
RUN mkdir -p /opt/MediathekView \
 && case "$TARGETARCH" in \
      arm64) ARCH="linux-aarch64" ;; \
      amd64) ARCH="linux" ;; \
      *) echo "Unsupported arch: $TARGETARCH" && exit 1 ;; \
    esac \
 && wget -q "https://download.mediathekview.de/stabil/MediathekView-$(cat /tmp/mediathekview.version)-${ARCH}.tar.gz" -O /tmp/MediathekView.tar.gz \
 && tar xf /tmp/MediathekView.tar.gz -C /opt \
 && rm /tmp/MediathekView.tar.gz /tmp/mediathekview.version
