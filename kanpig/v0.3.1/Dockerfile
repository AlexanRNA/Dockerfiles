FROM rust:1.82

# for easy upgrade later. ARG variables only persist during image build time
ARG KANPIGVER="v0.3.1"

# metadata
LABEL base.image="rust:1.82"
LABEL dockerfile.version="1"
LABEL software="kanpig"
LABEL software.version="0.3.1"
LABEL website="https://github.com/ACEnglish/kanpig"
LABEL license="https://github.com/ACEnglish/kanpig/blob/develop/LICENSE"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"


RUN wget https://github.com/ACEnglish/kanpig/releases/download/${KANPIGVER}/kanpig-${KANPIGVER}-x86_64-unknown-linux-musl.tar.gz

RUN tar -xf kanpig-${KANPIGVER}-x86_64-unknown-linux-musl.tar.gz

RUN rm kanpig-${KANPIGVER}-x86_64-unknown-linux-musl.tar.gz && mv kanpig* /opt/kanpig/ && \
    cd /opt/kanpig

ENV PATH=/opt/kanpig/:$PATH
