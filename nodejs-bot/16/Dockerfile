FROM        --platform=$TARGETOS/$TARGETARCH node:16-bullseye-slim

LABEL       author="Mateus Colli" maintainer="mateusambrosino@gmail.com"

#  Desabilita o Download do Chromium pelo puppeter
ENV         PUPPETEER_SKIP_DOWNLOAD true
ENV         PUPPETEER_SKIP_CHROMIUM_DOWNLOAD true
ENV         TZ="America/Sao_Paulo"

# RUN         apt update \
#             && apt -y install ffmpeg iproute2 git sqlite3  libsqlite3-dev python3 python3-dev ca-certificates dnsutils tzdata zip tar curl build-essential libtool wget xvfb \
#             && npm -g install npm@latest \
#             && useradd -m -d /home/container container
            
# RUN         wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
#             && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
#             && apt-get update -qqy \
#             && apt-get -qqy install

RUN         apt-get update && \
            apt-get install -y gnupg wget curl unzip --no-install-recommends && \
            wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
            echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list && \
            apt-get update -y && \
            apt-get install -y google-chrome-stable

# Baixando google chrome
# RUN         wget -q https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
# RUN         apt-get install -y ./google-chrome-stable_current_amd64.deb

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]