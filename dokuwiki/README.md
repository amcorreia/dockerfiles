amcorreia/dokuwiki
==================

[![Docker Stars](https://img.shields.io/docker/stars/amcorreia/dokuwiki.svg)](https://hub.docker.com/r/amcorreia/dokuwiki/)
[![Docker Pulls](https://img.shields.io/docker/pulls/amcorreia/dokuwiki.svg)](https://hub.docker.com/r/amcorreia/dokuwiki/)
[![Docker Build](https://img.shields.io/docker/automated/amcorreia/dokuwiki.svg)](https://hub.docker.com/r/amcorreia/dokuwiki/)
[![Layers](https://images.microbadger.com/badges/image/amcorreia/dokuwiki.svg)](https://microbadger.com/images/amcorreia/dokuwiki)
[![Version](https://images.microbadger.com/badges/version/amcorreia/dokuwiki.svg)](https://microbadger.com/images/amcorreia/dokuwiki)

Docker container image with [DokuWiki](https://www.dokuwiki.org/dokuwiki) and lighttpd

### How to run

Assume your docker host is localhost and HTTP public port is 80 (change these values if you need).

First, run new dokuwiki container:

    docker run -d -p 80:80 --name wiki amcorreia/dokuwiki

