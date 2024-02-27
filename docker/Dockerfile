ARG RELEASE="bookworm-slim"
FROM debian:$RELEASE as addons

WORKDIR /addons

RUN set -ex && apt update && apt install -yq git

RUN set -ex \
    && git clone --depth 1 --branch 3.0.1 https://github.com/romanvm/plugin.video.example.git \
    && git clone --depth 1 https://github.com/kyzima-spb/kodi.repository.git /tmp/repo \
    && mv /tmp/repo/addons/repository.kirill.vercetti .


ARG RELEASE="bookworm-slim"

FROM kyzimaspb/gui:$RELEASE

LABEL maintainer="Kirill Vercetti <office@kyzima-spb.com>"

WORKDIR /home/user

RUN set -ex && mkdir -p .kodi/addons

USER root

RUN set -ex \
    && apt update \
    && apt install -yq kodi \
    && apt-get clean  \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY --from=addons /addons .kodi/addons/
COPY ./root /

USER user
