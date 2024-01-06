ARG BASE_IMAGE

FROM ${BASE_IMAGE}

ARG URL
ARG CORE

# OS dependencies and packages

RUN \
  apt-get -y update \
  && apt-get -y install --no-install-recommends \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Arduino CLI

RUN \
  arduino-cli core update-index ${URL} \
  && arduino-cli core install ${CORE}