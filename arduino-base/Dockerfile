FROM debian:stable-slim

# OS dependencies and packages

RUN \
  apt-get -y update \
  && apt-get -y install --no-install-recommends \
  ca-certificates \
  curl \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Arduino CLI

RUN \
  curl -fsSL https://raw.githubusercontent.com/arduino/arduino-cli/master/install.sh | BINDIR=/usr/bin sh \
  && arduino-cli update