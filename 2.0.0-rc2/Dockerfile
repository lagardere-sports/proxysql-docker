FROM debian:stretch
MAINTAINER Ashraf Sharif <ashraf@severalnines.com>

ENV VERSION 2.0.0-rc2
ENV DEB_PACKAGE proxysql-rc2_2.0.0-debian9_amd64

RUN apt-get update && \
    apt-get install -y wget mysql-client inotify-tools procps && \
    wget https://github.com/sysown/proxysql/releases/download/v${VERSION}/${DEB_PACKAGE}.deb -O /opt/proxysql_${VERSION}-debian9_amd64.deb && \
    dpkg -i /opt/proxysql_${VERSION}-debian9_amd64.deb && \
    rm -f /opt/proxysql_${VERSION}-debian9_amd64.deb && \
    rm -rf /var/lib/apt/lists/*

VOLUME /var/lib/proxysql
EXPOSE 6032 6033

COPY proxysql_galera_checker.sh /usr/share/proxysql/tools/
COPY entrypoint.sh /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
