FROM rocker/tidyverse:4.3.1

LABEL base.image="rocker/tidyverse:4.3.1"
LABEL dockerfile.version="2"
LABEL software="R"
LABEL software.version="4.3.1"
LABEL description="R envirnment for genomic visualisation"
LABEL website="https://www.r-project.org/"
LABEL license="https://www.r-project.org/Licenses/"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

RUN R -e "install.packages(c('readr','rtracklayer'))"

RUN R -e "if (!require('BiocManager', quietly = TRUE)) install.packages('BiocManager')"
RUN R -e "BiocManager::install('rtracklayer')"