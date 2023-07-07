FROM ubuntu:lunar

# for easy upgrade later. ARG variables only persist during image build
ARG JASMINEVER="62b7054"


LABEL base.image="ubuntu:lunar"
LABEL dockerfile.version="1"
LABEL software="Jasmine"
LABEL software.version="62b7054"
LABEL description="Jasmine: SV Merging Across Samples. Modified IRIS version by alexanrna"
LABEL website="https://github.com/AlexanRNA/Jasmine"
LABEL license="https://github.com/AlexanRNA/Jasmine/blob/master/LICENSE"
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



# install Iris and Jasmina
RUN git clone --recursive https://github.com/AlexanRNA/Jasmine.git && \
    cd Jasmine && \
    git reset --hard ${JASMINEVER} && \
    cd Iris && \
    chmod +x rebuild_default_external.sh && \
    ./rebuild_default_external.sh && \
    chmod +x build.sh && \
    ./build.sh

# build Jasmine from source
RUN  cd Jasmine && chmod +x  ./build_jar.sh && ./build_jar.sh


# set perl locale settings
CMD [ "jasmine" ]