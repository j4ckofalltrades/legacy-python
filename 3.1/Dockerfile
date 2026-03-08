FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential patch python2 wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/3.1/Python-3.1.tgz
RUN tar -xf Python-3.1.tgz
WORKDIR /tmp/Python-3.1

COPY diff.patch diff.patch
RUN patch -p0 < diff.patch
RUN ./configure
RUN make install
WORKDIR /

CMD ["python3"]
