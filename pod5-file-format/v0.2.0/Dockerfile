FROM python:3.10

LABEL base.image="python:3.10"
LABEL dockerfile.version="1"
LABEL software="pod5tools"
LABEL software.version="0.2.0"
LABEL description="Pod5: a high performance file format for nanopore reads."
LABEL website="https://github.com/nanoporetech/pod5-file-format"
LABEL license="https://github.com/nanoporetech/pod5-file-format/blob/master/LICENSE.md"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

# for easy upgrade later. ARG variables only persist during image build
ARG POD5TOOLSVER=0.2.0

WORKDIR /usr/src/app

RUN pip install --no-cache-dir --upgrade pip && \
    pip install --no-cache-dir pod5==${POD5TOOLSVER}
