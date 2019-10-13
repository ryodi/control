FROM vault:latest

ENV SKIP_CHOWN=y SKIP_SETCAP=y
RUN setcap cap_ipc_lock=+ep $(readlink -f $(which vault))
