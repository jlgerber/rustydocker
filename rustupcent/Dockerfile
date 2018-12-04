FROM centos:7.5.1804
# set the version you want to build using
# docker  build --build-arg RUST_VERSION==a_value
# eg
# docker build --build-arg RUST_VERSION=nightly-2018-11-11
MAINTAINER jgerber <jgerber@d2.com>

WORKDIR /root

# common packages
RUN yum -y update && \
    yum -y install  \
    ca-certificates curl file \
    build-essential make \
    autoconf automake autotools-dev libtool xutils-dev

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
ENV UID ""
ENV GID ""
ENV FLAG ""
ENTRYPOINT sh -c "cargo build ${FLAG:---release} && find ./target -exec chown ${UID}:{GID} {} \;"