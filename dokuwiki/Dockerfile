# Ripped from: https://bitbucket.org/mprasil/docker_dokuwiki/src/96330e626964?at=master
#
# DESCRIPTION:    Image with DokuWiki & lighttpd
# TO_BUILD:       docker build -t amcorreia/dokuwiki .
# TO_RUN:         docker run -d -p 80:80 --name wiki amcorreia/dokuwiki

# Base docker image
FROM alpine
MAINTAINER  Alessandro Madruga Correia <mutley.sandro@gmail.com>

# Set the version you want of Twiki
ENV DOKUWIKI_VERSION stable
ENV DOKUWIKI_CSUM 9b9ad79421a1bdad9c133e859140f3f2

# Update & install packages & cleanup afterwards
#RUN adduser -D lighttpd lighttpd
RUN set -x && apk add --update --no-cache wget lighttpd php5-cgi php5-gd tar && \
    wget --no-check-certificate -q -O /dokuwiki.tgz "https://download.dokuwiki.org/src/dokuwiki/dokuwiki-$DOKUWIKI_VERSION.tgz" && \
    if [ "$DOKUWIKI_CSUM" != "$(md5sum /dokuwiki.tgz | awk '{print($1)}')" ];then echo "Wrong md5sum of downloaded file!"; exit 1; fi && \
    mkdir /dokuwiki && \
    tar -zxf dokuwiki.tgz -C /dokuwiki --strip-components 1 && \
    rm dokuwiki.tgz && \
    chown -R lighttpd:lighttpd /dokuwiki && \
    mkdir /var/run/lighttpd && \
    chown lighttpd:lighttpd /var/run/lighttpd && \
    echo 'include "dokuwiki.conf"' >> /etc/lighttpd/lighttpd.conf

# Configure lighttpd
ADD dokuwiki.conf /etc/lighttpd/dokuwiki.conf

EXPOSE 80
VOLUME ["/dokuwiki/data/","/dokuwiki/lib/plugins/","/dokuwiki/conf/","/dokuwiki/lib/tpl/","/var/log/"]

ENTRYPOINT ["/usr/sbin/lighttpd", "-D", "-f", "/etc/lighttpd/lighttpd.conf"]
