FROM jgerber/rustup:nightly-2018-11-12

RUN apt-get update && \
    apt-get install --no-install-recommends -y \
    python3 \
    python2.7 \
    python-pip \
    python3-pip \
    python3-dev \
    python-dev

RUN pip install pyo3-pack

ENTRYPOINT ["pyo3-pack"]
CMD ["build"]