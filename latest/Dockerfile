FROM        --platform=$TARGETOS/$TARGETARCH rust:slim

LABEL       author="Channing Babb" maintainer="channingbabb@gmail.com"

RUN         apt update \
                && apt -y install git dnsutils curl iproute2 ffmpeg tini libssl-dev pkg-config  \
                && useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container CARGO_HOME=/home/container/.cargo PKG_CONFIG_PATH=/usr/lib/pkgconfig
WORKDIR     /home/container

COPY        --chown=container:container ./../entrypoint.sh /entrypoint.sh
RUN         chmod +x /entrypoint.sh
ENTRYPOINT    ["/usr/bin/tini", "-g", "--"]
CMD         ["/entrypoint.sh"]