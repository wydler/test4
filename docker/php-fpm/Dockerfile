############################
# Stage 1: Runtime
############################
FROM php:8.4.1-fpm@sha256:319fef0a241cb9ff1afd0b8c689633214be7c3bb4a4029c305dec103b5695d6b

############################
# Metadata
############################
LABEL maintainer="Daniel Wydler" \
      org.opencontainers.image.authors="Daniel Wydler" \
      org.opencontainers.image.description="A user-friendly PHP Looking Glass - Reloaded" \
      org.opencontainers.image.documentation="https://github.com/dwydler/LookingGlass-Docker/blob/master/README.md" \
      org.opencontainers.image.source="https://github.com/dwydler/LookingGlass-Docker" \
      org.opencontainers.image.title="lookingglass-php" \
      org.opencontainers.image.url="https://hub.docker.com/r/wydler/lookingglass-php"

############################
# System dependencies
############################
RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        net-tools \
        host \
        mtr \
        iputils-ping \
        traceroute \
        locales \
    && rm -rf /var/lib/apt/lists/*

############################
# PHP extensions
############################
RUN docker-php-ext-install -j"$(nproc)" gettext

############################
# Locale configuration
############################
RUN sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && sed -i -e 's/# de_DE.UTF-8 UTF-8/de_DE.UTF-8 UTF-8/' /etc/locale.gen \
    && locale-gen

RUN locale-gen de_DE.UTF-8 en_US.UTF-8
