# Reference image
FROM ubuntu:22.10@sha256:e322f4808315c387868a9135beeb11435b5b83130a8599fd7d0014452c34f489

# Metadata
LABEL org.opencontainers.image.authors="Daniel Wydler"

# Package lists reread and updated
# Install package(s)
# Remove the package lists
RUN apt-get update && \
    apt-get install -y \
    uwsgi \
    uwsgi-plugin-python3 \
    python3-dnspython \
    net-tools \
    iputils-ping \
    python3-pip \
    && rm -r /var/lib/apt/lists/*

#
RUN pip3 --no-cache-dir install \
    setuptools \
    wheel \
    uwsgitop \
    Flask-Limiter

#
RUN mkdir -p /etc/uwsgi/vassals \
    && chmod 755 /etc/uwsgi/vassals

#
RUN mkdir -p /etc/uwsgi/apps-enabled

#
CMD ["/usr/bin/uwsgi", "--ini", "/etc/uwsgi/vassals/mta-sts.ini"]
