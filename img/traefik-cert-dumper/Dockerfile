FROM golang:1-alpine AS stage1

RUN apk update \
 && apk --no-cache --no-progress add git make gcc musl-dev \
 && mkdir -p /go/src/github.com/ldez/ \
 && cd /go/src/github.com/ldez/ \
 && git clone https://github.com/ldez/traefik-certs-dumper

WORKDIR /go/src/github.com/ldez/traefik-certs-dumper
RUN go mod download
RUN make build

#########################################################

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

COPY --from=stage1 /go/src/github.com/ldez/traefik-certs-dumper/traefik-certs-dumper /bin/traefik-certs-dumper
COPY overlay/ /
COPY CHANGELOG /var/lib/ryodi/

ENTRYPOINT ["/bin/ryodi-go"]
