FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/2.5/Python-2.5.tgz
RUN tar -xf Python-2.5.tgz
WORKDIR /tmp/Python-2.5

RUN ./configure
RUN make install
WORKDIR /

CMD ["python"]
