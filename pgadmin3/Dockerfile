FROM ubuntu:xenial
MAINTAINER zfil

ENV LANG C.UTF-8

RUN apt-get update && apt-get install -y pgadmin3 --no-install-recommends && rm -rf /var/lib/apt/lists/*
RUN useradd -m pgadmin3

WORKDIR /home/pgadmin3

USER pgadmin3
ENV HOME /home/pgadmin3

CMD pgadmin3
