FROM ubuntu:focal

# for easy upgrade later. ARG variables only persist during image build
ARG BCFTOOLSVER=1.20

LABEL base.image="ubuntu:focal"
LABEL dockerfile.version="1"
LABEL software="bcftools"
LABEL software.version="1.20"
LABEL description="Tools (written in C using htslib) for manipulating next-generation sequencing data"
LABEL website="https://github.com/samtools/bcftools"
LABEL license="https://github.com/samtools/bcftools/blob/develop/LICENSE"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

ENV TZ=Europe/Brussels
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# install dependencies and clean up apt garbage
RUN apt-get update && apt-get install --no-install-recommends -y \
 libncurses5-dev \
 libbz2-dev \
 libgsl-dev \
 liblzma-dev \
 libcurl4-gnutls-dev \
 zlib1g-dev \
 libssl-dev \
 gcc \
 wget \
 make \
 perl \
 libperl-dev \
 bzip2 \
 gnuplot \
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*

# install samtools, make /data
RUN wget https://github.com/samtools/bcftools/releases/download/${BCFTOOLSVER}/bcftools-${BCFTOOLSVER}.tar.bz2 && \
 tar -xjf bcftools-${BCFTOOLSVER}.tar.bz2 && \
 rm bcftools-${BCFTOOLSVER}.tar.bz2 && \
 cd bcftools-${BCFTOOLSVER} && \
 ./configure --prefix=/usr --enable-perl-filters --enable-libgsl && \
 make && \
 make install && \
 cd htslib-${BCFTOOLSVER} && make && mv tabix /usr/bin && mv bgzip /usr/bin && \
 cd / && rm -rf bcftools-${BCFTOOLSVER}

# set perl locale settings
ENV LC_ALL=C

CMD [ 'bcftools' ]