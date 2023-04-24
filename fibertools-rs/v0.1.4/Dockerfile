FROM  continuumio/miniconda3

LABEL base.image="continuumio/miniconda3"
LABEL dockerfile.version="1"
LABEL software="fibertools-rs"
LABEL software.version="0.1.4"
LABEL description="a CLI tool for creating and interacting with fiberseq bam files."
LABEL website="https://github.com/fiberseq/fibertools-rs"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"


ENV TZ=Europe/Brussels
# RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

RUN conda install -c conda-forge -c bioconda fibertools-rs && \
    conda clean --all --yes