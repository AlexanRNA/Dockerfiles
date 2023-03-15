FROM rocker/tidyverse:4.0.2

LABEL base.image="rocker/tidyverse:4.0.2"
LABEL dockerfile.version="1"
LABEL software="R"
LABEL software.version="4.2.2"
LABEL description="R envirnment for visualisation"
LABEL website="https://www.r-project.org/"
LABEL license="https://www.r-project.org/Licenses/"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

RUN R -e "install.packages(c('gridExtra'))"