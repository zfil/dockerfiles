FROM ubuntu:xenial

# Default to UTF-8 file.encoding
ENV LANG C.UTF-8

# Add extra repositories
RUN apt-get update -qq \
    && apt-get install -y -qq apt-transport-https curl \
    && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 \
    && echo "deb https://dl.bintray.com/sbt/debian /" > /etc/apt/sources.list.d/sbt.list \
    && curl -sS https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - \
    && echo "deb https://deb.nodesource.com/node_8.x xenial main" > /etc/apt/sources.list.d/nodesource.list \
    && curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
    && echo "deb https://dl.yarnpkg.com/debian/ stable main" > /etc/apt/sources.list.d/yarn.list \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

ENV JDK_VERSION "8u151*"
ENV SBT_VERSION "1.1.*"
ENV YARN_VERSION "1.*"

RUN apt-get update -qq \
    && apt-get install -y -qq bc \
    && apt-get install -y -qq jq \
    && apt-get install -y -qq openjdk-8-jdk-headless=${JDK_VERSION} \
    && apt-get install -y -qq sbt=${SBT_VERSION} \
    && apt-get install -y -qq nodejs yarn=${YARN_VERSION} \
    && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*

ENV DOCKER_VERSION 17.12.0

RUN set -x \
    && curl -sfSL "https://download.docker.com/linux/static/stable/x86_64/docker-${DOCKER_VERSION}-ce.tgz" -o docker.tgz \
    && tar -xzvf docker.tgz \
    && mv docker/* /usr/local/bin/ \
    && rmdir docker \
    && rm docker.tgz \
    && chmod +s /usr/local/bin/docker

RUN curl -sfSL https://bootstrap.pypa.io/get-pip.py | python \
    && /usr/local/bin/pip install awscli
