FROM --platform=$TARGETOS/$TARGETARCH elixir:slim

LABEL author="Tallo" maintainer="tallo@tallostudios.com"

RUN  apt update \
            && apt -y install git dnsutils curl iproute2 ffmpeg tini \
     		&& apt -y install build-essential erlang-dev gcc make --no-install-recommends \
            && useradd -m -d /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

STOPSIGNAL SIGINT

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]
