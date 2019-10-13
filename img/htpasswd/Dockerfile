FROM alpine:3

RUN mkdir -p /d/bin \
 && apk update \
 && apk add apache2-utils \
 && rm -rf /var/cache/apk/*

ENTRYPOINT ["/usr/bin/htpasswd"]
