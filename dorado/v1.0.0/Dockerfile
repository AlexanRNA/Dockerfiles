FROM ubuntu:plucky


ARG DORADOVER=1.0.0
# ARG SAMTOOLSVER=1.20


LABEL base.image="ubuntu:plucky"
LABEL dockerfile.version="1"
LABEL software="Dorado"
LABEL software.version="1.0.0"
LABEL description="Dorado is a high-performance, easy-to-use, open source basecaller for Oxford Nanopore reads."
LABEL website="https://github.com/nanoporetech/dorado"
LABEL license="https://github.com/nanoporetech/dorado/blob/master/LICENCE.txt"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"


RUN apt-get update && apt-get install -y autoconf --no-install-recommends -y \
 libncurses5-dev \
 libbz2-dev \
 liblzma-dev \
 libcurl4-gnutls-dev \
 zlib1g-dev \
 libssl-dev \
 gcc \
 tzdata \
 wget \
 make \
 bc \
 perl \
 bzip2 \
 gnuplot \
 libqt5core5a \
 python3 \
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*

ENV TZ=Europe/Brussels
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone


# get plot-bamstats to work
RUN strip --remove-section=.note.ABI-tag /usr/lib/x86_64-linux-gnu/libQt5Core.so.5

RUN wget https://cdn.oxfordnanoportal.com/software/analysis/dorado-${DORADOVER}-linux-x64.tar.gz && \
    tar -xf dorado-${DORADOVER}-linux-x64.tar.gz && \
    rm dorado-${DORADOVER}-linux-x64.tar.gz && mv dorado* /opt/dorado && \
    cd /opt/dorado/bin && ./dorado download --model all

ENV PATH=/opt/dorado/bin/:$PATH
    

ENV LC_ALL=C
# get python
RUN apt-get update && apt-get install -y autoconf --no-install-recommends -y \
python3

RUN apt-get update && apt-get install -y autoconf --no-install-recommends -y \
    git
