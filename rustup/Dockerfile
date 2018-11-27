FROM ubuntu as build
# set the version you want to build using
# docker  build --build-arg RUST_VERSION==a_value
# eg
# docker build --build-arg RUST_VERSION=nightly-2018-11-11
MAINTAINER Liu Chong <mail@clojure.cn>

WORKDIR /root

# common packages
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    ca-certificates curl file \
    build-essential \
    autoconf automake autotools-dev libtool xutils-dev && \
    rm -rf /var/lib/apt/lists/*

ENV SSL_VERSION=1.0.2p

RUN curl https://www.openssl.org/source/openssl-$SSL_VERSION.tar.gz -O && \
    tar -xzf openssl-$SSL_VERSION.tar.gz && \
    cd openssl-$SSL_VERSION && ./config && make depend && make install && \
    cd .. && rm -rf openssl-$SSL_VERSION*

ENV OPENSSL_LIB_DIR=/usr/local/ssl/lib \
    OPENSSL_INCLUDE_DIR=/usr/local/ssl/include \
    OPENSSL_STATIC=1

ARG RUST_VERSION

# install toolchain
RUN curl https://sh.rustup.rs -sSf | \
    sh -s -- --default-toolchain ${RUST_VERSION} -y

ENV PATH=/root/.cargo/bin:$PATH
#RUN rustup install ${RUST_VERSION}
