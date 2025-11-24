FROM rust:1.79

# for easy upgrade later. ARG variables only persist during image build time
ARG MODKITVER="v0.5.0"

# metadata
LABEL base.image="rust:buster"
LABEL dockerfile.version="1"
LABEL software="modkit"
LABEL software.version="0.5.1-rc1"
LABEL website="https://github.com/nanoporetech/modkit"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"


RUN wget https://github.com/nanoporetech/modkit/releases/download/${MODKITVER}/modkit_${MODKITVER}_u16_x86_64.tar.gz
 

RUN tar -xf modkit_${MODKITVER}_u16_x86_64.tar.gz 

RUN rm modkit_${MODKITVER}_u16_x86_64.tar.gz && mv dist* /opt/dist/ && \
    cd /opt/dist

ENV PATH=/opt/dist/:$PATH