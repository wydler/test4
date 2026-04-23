# Reference image
FROM alpine:3.23.2@sha256:865b95f46d98cf867a156fe4a135ad3fe50d2056aa3f25ed31662dff6da4eb62

# Metadata
LABEL maintainer="Daniel Wydler"
LABEL org.opencontainers.image.authors="Daniel Wydler"
LABEL org.opencontainers.image.description="A Python package and CLI for parsing aggregate and forensic DMARC reports."
LABEL org.opencontainers.image.documentation="https://github.com/dwydler/parsedmarc-docker/blob/master/README.md"
LABEL org.opencontainers.image.source="https://github.com/dwydler/parsedmarc-docker"
LABEL org.opencontainers.image.title="wydler/parsedmarc-utils"
LABEL org.opencontainers.image.url="https://github.com/dwydler/parsedmarc-docker"

# Install minimal runtime dependencies (bash, curl) without caching package index
RUN apk add --no-cache \
        bash \
        curl

# Kibana export file for later import/use inside container
COPY docker/kibana/export.ndjson /tmp/

#ENTRYPOINT [ "/bin/sh", "-c", "--" , "while true; do sleep 30; done;" ]
# Default command: start Bash shell
CMD ["/bin/bash"]
