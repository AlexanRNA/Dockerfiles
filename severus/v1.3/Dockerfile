FROM continuumio/miniconda3:24.11.1-0
SHELL ["/bin/bash", "-c"]

ARG SEVVER="1.3"

# metadata
LABEL base.image="continuumio/miniconda3:24.11.1-0"
LABEL dockerfile.version="1"
LABEL software="severus"
LABEL software.version="1.3"
LABEL website="https://github.com/KolmogorovLab/Severus"
LABEL license="https://github.com/KolmogorovLab/Severus?tab=License-1-ov-file#readme"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

RUN apt-get update && \
    apt-get install -y wget build-essential curl libncurses5-dev zlib1g-dev libbz2-dev liblzma-dev git unzip && \
    apt-get install --no-install-recommends -y lsb-release gnupg && \
    apt-get -qq -y autoremove && \
    apt-get clean


RUN conda install -y ipykernel python=3.11
RUN conda config --add channels bioconda
RUN conda config --add channels conda-forge
RUN conda install severus


ENV PATH=/opt/vartrix:/opt:$PATH
