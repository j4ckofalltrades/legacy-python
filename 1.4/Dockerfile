FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential libcrypt-dev patch wget -y
WORKDIR /tmp

RUN wget https://legacy.python.org/download/releases/src/python-1.4.tar.gz
RUN tar -xf python-1.4.tar.gz
WORKDIR /tmp/Python-1.4

COPY diff.patch diff.patch
RUN patch -p0 < diff.patch
RUN ./configure
RUN make install
WORKDIR /

CMD ["python"]
