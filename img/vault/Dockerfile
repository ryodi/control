FROM vault:latest

ARG version
ARG builddate
ARG commitish
ARG repository

LABEL com.ryodi.img.version="$version"
LABEL com.ryodi.img.builddate="$builddate"
LABEL com.ryodi.img.repository="$repository"
LABEL com.ryodi.img.commitish="$commitish"
LABEL maintainer="The RYODI Project <images@ryodi.com>"


ENV SKIP_CHOWN=y SKIP_SETCAP=y
RUN setcap cap_ipc_lock=+ep $(readlink -f $(which vault))
