FROM        --platform=$TARGETOS/$TARGETARCH node:16-bullseye-slim

LABEL       author="Mateus Colli" maintainer="mateusambrosino@gmail.com"

#  Desabilita o Download do Chromium pelo puppeter
ENV         PUPPETEER_SKIP_DOWNLOAD true
ENV         PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true
ENV         TZ="America/Sao_Paulo"

RUN         apt update \
            && apt -y install ffmpeg iproute2 git sqlite3 libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool wget \
            && npm -g install npm@latest \
            && useradd -m -d /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

# Baixando google chrome
RUN         wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb -P /home/container

# Instalando google chrome
RUN         apt install -y /home/container/google-chrome-stable_current_amd64.deb

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]