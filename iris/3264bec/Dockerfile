FROM ubuntu:lunar

LABEL base.image="ubuntu:lunar"
LABEL dockerfile.version="1"
LABEL software="Iris"
LABEL software.version="3264bec"
LABEL description="A module for improving the insertion sequences of structural variant calls"
LABEL website="https://github.com/mkirsche/Iris"
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
 perl \
 autoconf \
 automake \ 
 libperl-dev \
 default-jre \
 default-jdk \
 ca-certificates && \
 apt-get autoclean && rm -rf /var/lib/apt/lists/*

 # install iris

# Clone the Iris repository
RUN git clone --recursive https://github.com/AlexanRNA/Iris.git /Iris

# Build Iris
WORKDIR /Iris
RUN chmod +x rebuild_default_external.sh && \
    ./rebuild_default_external.sh

RUN chmod +x build.sh && \
    ./build.sh


# Set the entry point and command
ENTRYPOINT ["java", "-cp", "/Iris/src", "Iris"]
CMD ["-h"]
