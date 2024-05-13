FROM python:3.10

# for easy upgrade later. ARG variables only persist during image build
ARG SNIFFLESVER=v2.3.3


# metadata
LABEL base.image="python:3.10"
LABEL dockerfile.version="1"
LABEL software="Sniffles"
LABEL software.version="2.3.3"
LABEL description="Sniffles is a structural variation caller using third generation sequencing (PacBio or Oxford Nanopore)."
LABEL website="https://github.com/fritzsedlazeck/Sniffles"
LABEL license="https://github.com/fritzsedlazeck/Sniffles?tab=License-1-ov-file#readme"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"



RUN wget https://github.com/fritzsedlazeck/Sniffles/archive/refs/tags/${SNIFFLESVER}.tar.gz && \
    tar -xf ${SNIFFLESVER}.tar.gz 

RUN pip install --no-cache-dir --upgrade pip && \ 
    pip install pysam ${SNIFFLESVER}.tar.gz

WORKDIR /usr/src/app

CMD [ "sniffles" ]


