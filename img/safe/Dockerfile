FROM alpine AS stage1

RUN mkdir -p /d/bin \
 && apk update \
 && apk add curl ca-certificates \
 && curl -sL https://github.com/starkandwayne/safe/releases/download/v1.3.4/safe-linux-amd64 -o /d/bin/safe \
 && curl -sL https://releases.hashicorp.com/vault/1.2.3/vault_1.2.3_linux_amd64.zip -o /vault.zip \
 && unzip /vault.zip \
 && mv vault /d/bin/vault \
 && chmod 0755 /d/bin/* \
 && cp /etc/ssl/cert.pem /d/ca.pem


FROM scratch

COPY --from=stage1 /d .

ENV PATH=/bin SSL_CERT_FILE=/ca.pem HOME=/home
ENTRYPOINT ["/bin/safe"]
