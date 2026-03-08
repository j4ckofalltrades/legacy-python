FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential wget zlib1g-dev -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/3.6.0/Python-3.6.0.tgz
RUN tar -xf Python-3.6.0.tgz
WORKDIR /tmp/Python-3.6.0

RUN ./configure
RUN make install
WORKDIR /

CMD ["python3"]
