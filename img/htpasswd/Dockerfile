FROM alpine:3

ARG version
ARG builddate
ARG commitish
ARG repository

LABEL com.ryodi.img.version="$version"
LABEL com.ryodi.img.builddate="$builddate"
LABEL com.ryodi.img.repository="$repository"
LABEL com.ryodi.img.commitish="$commitish"
LABEL maintainer="The RYODI Project <images@ryodi.com>"

RUN mkdir -p /d/bin \
 && apk update \
 && apk add apache2-utils \
 && rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/bin/htpasswd"]
