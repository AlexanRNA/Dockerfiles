FROM ubuntu:jammy

# for easy upgrade later. ARG variables only persist during image build time
ARG MODKITVER="v0.1.5"

# metadata
LABEL base.image="ubuntu:focal"
LABEL dockerfile.version="1"
LABEL software="modkit"
LABEL software.version="0.1.5"
LABEL website="https://github.com/nanoporetech/modkit"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

# install deps and cleanup apt garbage
# install dependencies and clean up apt garbage
RUN apt-get update && apt-get install --no-install-recommends -y \
 libncurses5-dev \
 libbz2-dev \
 liblzma-dev \
 libcurl4-gnutls-dev \
 zlib1g-dev \
 libssl-dev \
 gcc \
 wget \
 make \
 bc \
 perl \
 bzip2 \
 gnuplot \
 libqt5core5a \
 zip \
 unzip \ 
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*

RUN wget https://github.com/nanoporetech/modkit/releases/download/${MODKITVER}/modkit_centos7_x86_64.tar.gz 

RUN tar -xf modkit_centos7_x86_64.tar.gz 

RUN rm modkit_centos7_x86_64.tar.gz && mv dist* /opt/dist/ && \
    cd /opt/dist

ENV PATH=/opt/dist/:$PATH
