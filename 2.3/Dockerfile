FROM debian:bullseye
RUN set -x && \
    apt-get update && \
    apt-get install build-essential wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/2.3/Python-2.3.tgz
RUN tar -xf Python-2.3.tgz
WORKDIR /tmp/Python-2.3

RUN ./configure
RUN make install
WORKDIR /

CMD ["python"]
