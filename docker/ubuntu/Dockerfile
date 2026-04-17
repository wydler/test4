# Reference image
FROM ubuntu:22.04@sha256:c9672795a48854502d9dc0f1b719ac36dd99259a2f8ce425904a5cb4ae0d60d2

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
