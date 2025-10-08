FROM ubuntu:noble

# for easy upgrade later. ARG variables only persist during image build
ARG STRDUSTVER=0.11.1

LABEL base.image="ubuntu:noble"
LABEL dockerfile.version="1"
LABEL software="STRdust"
LABEL software.version="0.11.1"
LABEL description="Tandem repeat genotyping from long reads"
LABEL website="https://github.com/wdecoster/STRdust"
LABEL license="https://github.com/wdecoster/STRdust/blob/main/LICENSE"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

ENV TZ=Europe/Brussels
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

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

RUN wget https://github.com/wdecoster/STRdust/releases/download/v${STRDUSTVER}/STRdust-linux.zip && \
    unzip STRdust-linux.zip && \
    chmod +x STRdust && \
    mv STRdust /usr/local/bin/STRdust


ENV PATH="${PATH}:/STRdust/"

# set perl locale settings
ENV LC_ALL=C



