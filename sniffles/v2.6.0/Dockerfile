FROM python:3.10.15

# for easy upgrade later. ARG variables only persist during image build
ARG SNIFFLESVER=v2.6.0


# metadata
LABEL base.image="python:3.10"
LABEL dockerfile.version="3"
LABEL software="Sniffles"
LABEL software.version="2.6.0"
LABEL description="Sniffles is a structural variation caller using third generation sequencing (PacBio or Oxford Nanopore)."
LABEL website="https://github.com/fritzsedlazeck/Sniffles"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"



RUN wget https://github.com/fritzsedlazeck/Sniffles/archive/refs/tags/${SNIFFLESVER}.zip && \
    unzip ${SNIFFLESVER}.zip 

RUN pip install --no-cache-dir --upgrade pip && \ 
    pip install pysam ${SNIFFLESVER}.zip

WORKDIR /usr/src/app

CMD [ "sniffles" ]


