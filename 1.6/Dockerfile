FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential wget -y
WORKDIR /tmp

RUN wget https://legacy.python.org/download/releases/src/python-1.6.tar.gz
RUN tar -xf python-1.6.tar.gz
WORKDIR /tmp/Python-1.6

RUN ./configure
RUN make install
WORKDIR /

CMD ["python"]
