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
  arduino-cli config init \
  && if [ "$URL" != "" ] ; then arduino-cli config add board_manager.additional_urls ${URL} ; fi \
  && if [ "$VERSION" != "latest" ] ; then export CORE_FINAL="${CORE}@${VERSION}" ; else export CORE_FINAL="${CORE}" ; fi \
  && arduino-cli core update-index \
  && arduino-cli core install ${CORE_FINAL}