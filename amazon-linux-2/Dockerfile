# Amazon Linux 2
# Swift 5.4.1 Release
FROM amazonlinux:2
LABEL maintainer="Swift on Arm <docker@swift-arm.com>"
LABEL description="Docker Container for the Swift programming language"

RUN yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

RUN yum -y install \
  binutils \
  gcc \
  git \
  glibc-static \
  gzip \
  libbsd \
  libcurl \
  libedit \
  libicu \
  libsqlite3x \
  libstdc++-static \
  libuuid \
  libxml2 \
  python3 \
  tar \
  tzdata \
  zlib-devel

ARG SIGNING_KEY=D584E1710E48C09EEF94F463275C60777807339A
ARG PACKAGE_NAME=swiftlang-5.4.1-amazon-linux-2-release-aarch64-7-2021-05-28.tar.gz
ARG RELEASE_TAG=v5.4.1-RELEASE
ARG SWIFT_WEBROOT=https://github.com/futurejones/swift-arm64/releases/download/

ENV SIGNING_KEY=$SIGNING_KEY \
    PACKAGE_NAME=$PACKAGE_NAME \
    RELEASE_TAG=$RELEASE_TAG \
    SWIFT_WEBROOT=$SWIFT_WEBROOT


RUN set -e; \
    SWIFT_BIN_URL="$SWIFT_WEBROOT/$RELEASE_TAG/$PACKAGE_NAME" \
    && SWIFT_SIG_URL="$SWIFT_BIN_URL.sig" \
    # - Download the Swift toolchain
    && curl -fsSL "$SWIFT_BIN_URL" -o swift.tar.gz "$SWIFT_SIG_URL" -o swift.tar.gz.sig \
    && gpg --batch --quiet --keyserver hkp://keyserver.ubuntu.com:80 --recv $SIGNING_KEY \
    && gpg --batch --verify swift.tar.gz.sig swift.tar.gz \
    # - Unpack the toolchain, set libs permissions, and clean up.
    && tar -xzf swift.tar.gz --directory / \
    && chmod -R o+r /usr/lib/swift \
    && rm -rf swift.tar.gz swift.tar.gz.sig

# Print Installed Swift Version
RUN swift --version
