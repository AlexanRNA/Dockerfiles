# Dockerfile for tensorQTL
# from https://github.com/broadinstitute/tensorqtl/blob/master/Dockerfile, but bumped tensorqtl version to 1.0.10
FROM nvidia/cuda:12.1.1-cudnn8-runtime-ubuntu22.04
# MAINTAINER Francois Aguet
# version 2 with stats models added

RUN apt-get update && apt-get install -y software-properties-common && \
    apt-get update && apt-get install -y \
        apt-transport-https \
        build-essential \
        cmake \
        curl \
        libboost-all-dev \
        libbz2-dev \
        libcurl3-dev \
        liblzma-dev \
        libncurses5-dev \
        libssl-dev \
        python3 \
        python3-pip \
        sudo \
        unzip \
        wget \
        zlib1g-dev \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    apt-get clean && \
    apt-get autoremove -y && \
    rm -rf /var/lib/{apt,dpkg,cache,log}/

# htslib
RUN cd /opt && \
    wget --no-check-certificate https://github.com/samtools/htslib/releases/download/1.19/htslib-1.19.tar.bz2 && \
    tar -xf htslib-1.19.tar.bz2 && rm htslib-1.19.tar.bz2 && cd htslib-1.19 && \
    ./configure --enable-libcurl --enable-s3 --enable-plugins --enable-gcs && \
    make && make install && make clean

# bcftools
RUN cd /opt && \
    wget --no-check-certificate https://github.com/samtools/bcftools/releases/download/1.19/bcftools-1.19.tar.bz2 && \
    tar -xf bcftools-1.19.tar.bz2 && rm bcftools-1.19.tar.bz2 && cd bcftools-1.19 && \
    ./configure --with-htslib=system && make && make install && make clean

# install R
ENV DEBIAN_FRONTEND noninteractive
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
RUN add-apt-repository 'deb https://cloud.r-project.org/bin/linux/ubuntu jammy-cran40/'
RUN apt update && apt install -y r-base r-base-dev
ENV R_LIBS_USER=/opt/R/4.0
RUN Rscript -e 'if (!requireNamespace("BiocManager", quietly = TRUE)) {install.packages("BiocManager")}; BiocManager::install("qvalue");'

# python modules
RUN pip3 install --upgrade pip setuptools
RUN pip3 install numpy pandas scipy
RUN pip3 install pandas-plink ipython ipykernel jupyter matplotlib pyarrow torch rpy2 gcsfs Pgenlib>=0.90.1
RUN pip3 install tensorqtl==1.0.10
RUN pip3 install seaborn matplotlib

RUN pip3 install statsmodels


