FROM --platform=$TARGETOS/$TARGETARCH debian:trixie-slim

LABEL author="Matthew Penner" maintainer="matthew@pterodactyl.io"
LABEL org.opencontainers.image.source="https://github.com/pterodactyl/yolks"

ENV DEBIAN_FRONTEND=noninteractive

RUN dpkg --add-architecture i386 \
    && apt update \
    && apt upgrade -y \
    && apt install -y \
        tar curl gcc g++ lib32gcc-s1 libgcc1 \
        libcurl4-gnutls-dev:i386 libssl3:i386 libcurl4:i386 \
        lib32tinfo6 libtinfo6:i386 lib32z1 lib32stdc++6 \
        libncurses5:i386 libcurl3-gnutls:i386 libsdl2-2.0-0:i386 \
        iproute2 gdb libsdl1.2debian libfontconfig1 \
        telnet net-tools netcat-traditional tzdata \
        bash ca-certificates locales \
    && useradd -m -d /home/container container

RUN update-locale lang=en_US.UTF-8

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./entrypoint.sh /entrypoint.sh
CMD [ "/bin/bash", "/entrypoint.sh" ]