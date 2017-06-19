FROM ubuntu:xenial

RUN apt-get update \
    && apt-get -y install openjdk-8-jdk-headless \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

# Add Tini
ENV TINI_VERSION v0.14.0
ADD https://github.com/krallin/tini/releases/download/${TINI_VERSION}/tini /tini
RUN chmod +x /tini

ENTRYPOINT ["/tini", "--"]
