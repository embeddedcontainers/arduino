ARG BASE_IMAGE=arduino:base
ARG CORE
ARG VERSION
ARG URL

FROM ${BASE_IMAGE}

ARG CORE
ARG VERSION
ARG URL

# OS dependencies and packages

RUN \
  apt-get -y update \
  && apt-get -y install --no-install-recommends \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/*

# Arduino CLI

RUN \
  if [ "$URL" != "" ] ; then export URL_FINAL="--additional-urls ${URL}" ; else export URL_FINAL="" ; fi \
  && if [ "$VERSION" != "" ] ; then export CORE_FINAL="${CORE}@${VERSION}" ; else export CORE_FINAL="${CORE}" ; fi \
  && arduino-cli core update-index ${URL_FINAL} \
  && arduino-cli core install ${CORE_FINAL} ${URL_FINAL}