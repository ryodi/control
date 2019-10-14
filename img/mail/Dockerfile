FROM ubuntu:18.04

ARG version
ARG builddate
ARG commitish
ARG repository

LABEL com.ryodi.img.version="$version"
LABEL com.ryodi.img.builddate="$builddate"
LABEL com.ryodi.img.repository="$repository"
LABEL com.ryodi.img.commitish="$commitish"
LABEL maintainer="The RYODI Project <images@ryodi.com>"

RUN apt-get update \
 && echo "postfix postfix/mailname string example.com"             | debconf-set-selections \
 && echo "postfix postfix/main_mailer_type string 'Internet Site'" | debconf-set-selections \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y sqlite3 mailutils postfix postfix-pcre postfix-sqlite postgrey dovecot-core dovecot-sqlite dovecot-imapd dovecot-pop3d dovecot-sieve libdbi-perl libdbd-sqlite3-perl \
 && rm -rf /var/lib/apt/lists/* \
 && rm -rfv /etc/postfix/*.proto \
            /etc/postfix/*.d \
            /etc/dovecot/*.d

COPY bin/* /bin/

EXPOSE 25 587 110 995 143 993

CMD ["/bin/kickstart", "/bin/init", "-L", "/dev/log", \
                           "--", "postfix", "start-fg", \
                           "--", "dovecot", "-F", \
                           "--", "postgrey", "-q", "--inet=127.0.0.1:10023", "--delay=60"]
