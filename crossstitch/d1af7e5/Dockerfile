FROM ubuntu:lunar

# for easy upgrade later. ARG variables only persist during image build
ARG CROSSSTITCHVER="13595eb"
ARG HAPCUTVER="0eb7075"
ARG HTSLIBVER=1.17
ARG BCFTOOLSVER=1.17
ARG SAMTOOLSVER=1.17

LABEL base.image="ubuntu:lunar"
LABEL dockerfile.version="3"
LABEL software="CrossStitch"
LABEL software.version="13595eb"
LABEL description="CrossStitch creates personalized reference-quality diploid genomes without de novo assembly. Modified version by alexanrna"
LABEL website="https://github.com/schatzlab/crossstitch"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

ENV TZ=Europe/Brussels
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# install dependencies and clean up apt garbage
RUN apt-get update && apt-get install --no-install-recommends -y \
 libncurses5-dev \
 libbz2-dev \
 liblzma-dev \
 libgsl0-dev \
 libcurl4-gnutls-dev \
 zlib1g-dev \
 libssl-dev \
 gcc \
 git \
 g++ \
 wget \
 make \
 perl \
 bzip2 \
 pigz \
 autoconf \
 automake \ 
 libperl-dev \
 default-jre \
 default-jdk \
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*

 # install htslib (HAPCUT2 dependency)
RUN wget https://github.com/samtools/htslib/releases/download/${HTSLIBVER}/htslib-${HTSLIBVER}.tar.bz2 && \
    tar -xjf htslib-${HTSLIBVER}.tar.bz2 && \
    rm htslib-${HTSLIBVER}.tar.bz2 && \
    cd htslib-${HTSLIBVER} && \
    ./configure --prefix=/usr/ && \
    make && \
    make install

# install bcftools, make /data
RUN wget https://github.com/samtools/bcftools/releases/download/${BCFTOOLSVER}/bcftools-${BCFTOOLSVER}.tar.bz2 && \
    tar -xjf bcftools-${BCFTOOLSVER}.tar.bz2 && \
    rm bcftools-${BCFTOOLSVER}.tar.bz2 && \
    cd bcftools-${BCFTOOLSVER} && \
    ./configure --prefix=/usr --enable-perl-filters --enable-libgsl && \
    make && \
    make install && \
    cd htslib-${BCFTOOLSVER} && make && mv tabix /usr/bin && mv bgzip /usr/bin && \
    cd / && rm -rf bcftools-${BCFTOOLSVER}

# install samtools, make /data
RUN wget https://github.com/samtools/samtools/releases/download/${SAMTOOLSVER}/samtools-${SAMTOOLSVER}.tar.bz2 && \
    tar -xjf samtools-${SAMTOOLSVER}.tar.bz2 && \
    rm samtools-${SAMTOOLSVER}.tar.bz2 && \
    cd samtools-${SAMTOOLSVER} && \
    ./configure && \
    make && \
    make install && \
    mkdir /data


# install HapCUT2
RUN git clone --depth 1  https://github.com/vibansal/HapCUT2 && \
    cd HapCUT2 && git checkout ${HAPCUTVER} && \
    make && \
    mv /HapCUT2/build/HAPCUT2 /usr/bin && mv /HapCUT2/build/extractHAIRS /usr/bin

# install CrossStitch
RUN git clone --recursive https://github.com/AlexanRNA/crossstitch.git && \
    cd crossstitch && \
    git reset --hard ${CROSSSTITCHVER} && \
    cd vcf2diploid && \
    make && \
    cd ../Iris && \
    chmod +x rebuild_default_external.sh && \
    ./rebuild_default_external.sh && \
    chmod +x build.sh && \
    ./build.sh



RUN javac /crossstitch/src/*.java 
    

RUN chmod +x /crossstitch/src/crossstitch.sh

# set perl locale settings
CMD [ "/crossstitch/src/crossstitch.sh" ]