# Ubuntu Bionic 18.04
# Swift 5.4.0 Release
FROM ubuntu:18.04
LABEL maintainer="Swift on Arm <docker@swift-arm.com>"
LABEL description="Docker Container for the Swift programming language"

RUN export DEBIAN_FRONTEND=noninteractive DEBCONF_NONINTERACTIVE_SEEN=true && apt-get -q update && \
    apt-get -q install -y \
    binutils \
    git \
    gnupg2 \
    libc6-dev \
    libcurl4 \
    libedit2 \
    libgcc-5-dev \
    libpython3.6 \
    libsqlite3-0 \
    libstdc++-5-dev \
    libxml2 \
    libz3-dev \
    pkg-config \
    tzdata \
    zlib1g-dev \
    && rm -r /var/lib/apt/lists/*

ARG PACKAGE_NAME=swiftlang-5.4-ubuntu-18.04-release-aarch64-3-2021-04-26.tar.gz
ARG RELEASE_TAG=v5.4-RELEASE-2
ARG SWIFT_WEBROOT=https://github.com/futurejones/swift-arm64/releases/download/

ENV PACKAGE_NAME=$PACKAGE_NAME \
    RELEASE_TAG=$RELEASE_TAG \
    SWIFT_WEBROOT=$SWIFT_WEBROOT


RUN set -e; \
    SWIFT_BIN_URL="$SWIFT_WEBROOT/$RELEASE_TAG/$PACKAGE_NAME" \
    && SWIFT_SIG_URL="$SWIFT_BIN_URL.sig" \
    # -
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -q update && apt-get -q install -y curl && rm -rf /var/lib/apt/lists/* \
    # - Download the Swift toolchain
    && curl -fsSL "$SWIFT_BIN_URL" -o swift.tar.gz "$SWIFT_SIG_URL" -o swift.tar.gz.sig \
    && gpg --batch --quiet --auto-key-locate keyserver --locate-keys keys@swift-arm.com \
    && gpg --batch --verify swift.tar.gz.sig swift.tar.gz \
    # - Unpack the toolchain, set libs permissions, and clean up.
    && tar -xzf swift.tar.gz --directory / \
    && chmod -R o+r /usr/lib/swift \
    && rm -rf swift.tar.gz \
    && apt-get purge --auto-remove -y curl

# Print Installed Swift Version
RUN swift --version