FROM vault:latest
RUN setcap cap_ipc_lock=+ep $(readlink -f $(which vault))
