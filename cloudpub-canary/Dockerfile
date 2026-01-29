# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at https://mozilla.org/MPL/2.0/.

ARG BUILD_FROM=ghcr.io/hassio-addons/debian-base:9.2.0
FROM $BUILD_FROM

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

ARG BUILD_ARCH=amd64
ARG CLO_VERSION="3.0.2"

RUN \
    if [ "${BUILD_ARCH}" = "aarch64" ]; then CLO_ARCH="aarch64"; \
    elif [ "${BUILD_ARCH}" = "amd64" ]; then CLO_ARCH="x86_64"; \
    elif [ "${BUILD_ARCH}" = "armhf" ]; then CLO_ARCH="arm"; \
    elif [ "${BUILD_ARCH}" = "armv7" ]; then CLO_ARCH="arm"; \
    elif [ "${BUILD_ARCH}" = "i386" ]; then CLO_ARCH="i686"; fi \
    && cd /usr/bin \
    && curl -L "https://cloudpub.ru/download/stable/clo-${CLO_VERSION}-stable-linux-${CLO_ARCH}.tar.gz" | tar -x -z \
    && chmod +x /usr/bin/clo

COPY rootfs /

ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Black Roland <mail@roland.black>" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="Black Roland <mail@roland.black>" \
    org.opencontainers.image.authors="Black Roland <mail@roland.black>" \
    org.opencontainers.image.licenses="MPL-2.0" \
    org.opencontainers.image.url="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}
