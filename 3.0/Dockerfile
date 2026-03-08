FROM debian:bullseye
RUN set -x && \
    apt-get update && \
    apt-get install build-essential patch python2 wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/3.0/Python-3.0.tgz
RUN tar -xf Python-3.0.tgz
WORKDIR /tmp/Python-3.0

COPY diff.patch diff.patch
RUN patch -p0 < diff.patch
RUN ./configure
RUN make fullinstall
WORKDIR /

CMD ["python"]
