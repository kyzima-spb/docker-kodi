ARG RELEASE="bookworm-slim"

FROM kyzimaspb/gui:$RELEASE

LABEL maintainer="Kirill Vercetti <office@kyzima-spb.com>"

USER root

RUN set -ex \
    && apt update \
    && apt install -yq kodi \
    && apt-get clean  \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./root /

USER user

RUN set -ex \
    && mkdir -p /home/user/.kodi/addons
