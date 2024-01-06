ARG BASE_IMAGE
ARG CORE
ARG URL

FROM ${BASE_IMAGE}

ARG CORE
ARG URL

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