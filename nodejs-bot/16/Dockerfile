FROM        --platform=$TARGETOS/$TARGETARCH node:16

LABEL       author="Mateus Colli" maintainer="mateusambrosino@gmail.com"

#  Desabilita o Download do Chromium pelo puppeter
ENV         PUPPETEER_SKIP_DOWNLOAD true
ENV         PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true
ENV         TZ="America/Sao_Paulo"

RUN         apt update \
            && apt -y install ffmpeg iproute2 git sqlite3  libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool wget libnss3 libxcomposite1 xdg-utils libxss1 libappindicator1 libindicator7 \
            && npm -g install npm@latest \
            && useradd -m -d /home/container container

# Baixando google chrome
# RUN         wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
# RUN         apt-get install -y ./google-chrome-stable_current_amd64.deb

RUN         wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
RUN         dpkg -i google-chrome*.deb

RUN         apt-get install -f

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]