# Based on https://github.com/mide/minecraft-overviewer/blob/master/Dockerfile

FROM debian:stretch

LABEL org.opencontainers.image.source https://github.com/lmagomes/minecraft-containers

WORKDIR /home/minecraft/

RUN apt-get update && \
    apt-cache madison \
        build-essential \
        ca-certificates \
        curl \
        git \
        jq \
        optipng \
        python3-dev \
        python3-numpy \
        python3-pil \
        python3 \
        wget && \
    apt-get install -y --no-install-recommends \
        build-essential=12.9 \
        ca-certificates=20210119 \
        curl=7.74.0-1.3+deb11u7 \
        git=1:2.30.2-1+deb11u2 \
        jq=1.6-2.1 \
        python3-dev=3.9.2-3 \
        python3-numpy=1:1.19.5-1 \
        python3-pil=8.1.2+dfsg-0.3+deb11u1 \
        python3=3.9.2-3 \
        wget=1.21-1+deb11u1 && \
    apt-get install -y --no-install-recommends optipng=0.7.7-1+b1 || apt-get install -y --no-install-recommends optipng=0.7.7-1 && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    groupadd minecraft -g 1000 && \
    useradd -m minecraft -u 1000 -g 1000 && \
    mkdir -p /home/minecraft/render /home/minecraft/server

RUN git clone --depth=1 https://github.com/overviewer/Minecraft-Overviewer.git

WORKDIR /home/minecraft/Minecraft-Overviewer/
RUN python3 setup.py build && \
    python3 setup.py install

WORKDIR /home/minecraft/

RUN chown minecraft:minecraft -R /home/minecraft/

USER minecraft

CMD ["bash", "./overviewer.py"]