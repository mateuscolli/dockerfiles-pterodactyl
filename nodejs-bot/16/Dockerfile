FROM        --platform=$TARGETOS/$TARGETARCH node:16-bullseye-slim

LABEL       author="Mateus Colli" maintainer="mateusambrosino@gmail.com"

#  Desabilita o download do chromium pelo puppeter
ENV         PUPPETEER_SKIP_DOWNLOAD true
ENV         PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true
ENV         TZ="America/Sao_Paulo"

RUN         apt update \
            && apt -y install ffmpeg iproute2 git sqlite3  libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool wget xvfb \
            && npm -g install npm@latest \
            && npm -g install nodemon \
            && useradd -m -d /home/container container

# Instalando google chrome
RUN         wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN         apt-get install -y ./google-chrome-stable_current_amd64.deb

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]