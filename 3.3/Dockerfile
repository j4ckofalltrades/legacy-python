FROM debian:bullseye
LABEL org.opencontainers.image.source=https://github.com/j4ckofalltrades/legacy-python
RUN set -x && \
    apt-get update && \
    apt-get install build-essential patch wget -y
WORKDIR /tmp

RUN wget https://www.python.org/ftp/python/3.3.0/Python-3.3.0.tgz
RUN tar -xf Python-3.3.0.tgz
WORKDIR /tmp/Python-3.3.0

# Fix segfault in sysconfig generation caused by 8-byte alignment in obmalloc.c
# triggering misaligned SSE movaps instructions with GCC 10+ on 64-bit systems
COPY diff.patch diff.patch
RUN patch -p0 < diff.patch
RUN ./configure
RUN make install
WORKDIR /

CMD ["python3"]
