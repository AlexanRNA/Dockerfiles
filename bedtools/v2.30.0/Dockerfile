FROM ubuntu:kinetic

# for easy upgrade later. ARG variables only persist during image build time
ARG BEDVER="2.30.0"

# metadata
LABEL base.image="ubuntu:kinetic"
LABEL dockerfile.version="1"
LABEL software="bedtools"
LABEL software.version="2.30.0"
LABEL website="https://github.com/arq5x/bedtools2"
LABEL license = "https://github.com/arq5x/bedtools2/blob/master/LICENSE"
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
 bzip2 \
 perl \
 gnuplot \
 libqt5core5a \
 zip \
 g++ \
 unzip \ 
 python3 \
 bedtools \
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*




