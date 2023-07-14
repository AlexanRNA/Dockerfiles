FROM python:3.9

# for easy upgrade later. ARG variables only persist during image build
ARG SNIFFLESVER=v2.2


# metadata
LABEL base.image="python:3.9"
LABEL dockerfile.version="1"
LABEL software="Sniffles"
LABEL software.version="2.2"
LABEL description="Sniffles is a structural variation caller using third generation sequencing (PacBio or Oxford Nanopore)."
LABEL website="https://github.com/fritzsedlazeck/Sniffles"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"



RUN wget https://github.com/fritzsedlazeck/Sniffles/archive/refs/tags/v2.2.tar.gz && \
    tar -xf v2.2.tar.gz 

RUN pip install --no-cache-dir --upgrade pip && \ 
    pip install pysam v2.2.tar.gz

WORKDIR /usr/src/app

CMD [ "sniffles" ]


