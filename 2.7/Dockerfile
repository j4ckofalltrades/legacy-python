FROM debian:bullseye
RUN set -x && \
    apt-get update && \
    apt-get install build-essential wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/2.7/Python-2.7.tgz
RUN tar -xf Python-2.7.tgz
WORKDIR /tmp/Python-2.7

RUN ./configure
RUN make install
WORKDIR /

CMD ["python"]
