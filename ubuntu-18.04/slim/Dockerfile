# Ubuntu Bionic 18.04
# Swift-Slim 5.5.1 Release
FROM ubuntu:18.04
LABEL maintainer="Swift on Arm <docker@swift-arm.com>"
LABEL description="Docker Container for the Swift programming language"

RUN export DEBIAN_FRONTEND=noninteractive DEBCONF_NONINTERACTIVE_SEEN=true && apt-get -q update && \
    apt-get -q install -y \
    wget

ARG PACKAGE_NAME=swiftlang-slim_5.5.1-01-ubuntu-bionic_arm64.deb
ARG RELEASE_TAG=v5.5.1-RELEASE
ARG SWIFT_WEBROOT=https://archive.swiftlang.xyz/repos/ubuntu/pool/main/s/swiftlang-slim

RUN set -e; \
    SWIFT_BIN_URL="$SWIFT_WEBROOT/$PACKAGE_NAME" \
    # - download the swift toolchain
    && wget "$SWIFT_BIN_URL" \
    # - install swift
    && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -q install -y ./"$PACKAGE_NAME" \
    # - clean up.
    && rm -rf "$PACKAGE_NAME" \
    && apt-get purge --auto-remove -y wget \
    && rm -r /var/lib/apt/lists/*
