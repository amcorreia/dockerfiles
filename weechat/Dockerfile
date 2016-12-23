FROM alpine

RUN set -x && apk add --no-cache weechat

ENV LANG C.UTF-8
ENV HOME /home/user

RUN adduser -D user \
    && mkdir -p $HOME/.weechat \
    && chown -R user:user $HOME

WORKDIR $HOME
USER user

ENTRYPOINT ["weechat"]
