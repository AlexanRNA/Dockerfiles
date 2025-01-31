FROM ghcr.io/scverse/scvi-tools:py3.12-cu12-1.2.2.post2-dev


# metadata
LABEL base.image="ghcr.io/scverse/scvi-tools:py3.12-cu12-1.2.2.post2-dev"
LABEL dockerfile.version="6"
LABEL software="scvi-tools"
LABEL software.version="1.2.2.post2-dev"
LABEL website="https://github.com/scverse/scvi-tools"
LABEL license="https://github.com/scverse/scvi-tools/blob/main/LICENSE"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update

## INSTALL R
## INSTALL R
RUN apt update -y \
  && apt upgrade -y \
  && apt install -y \
  software-properties-common \
  dirmngr \
  gnupg2 \
  wget 


RUN wget -qO- https://cloud.r-project.org/bin/linux/ubuntu/marutter_pubkey.asc \
  | tee -a /etc/apt/trusted.gpg.d/cran_ubuntu_key.asc \
  && add-apt-repository -y "deb https://cloud.r-project.org/bin/linux/ubuntu $(lsb_release -cs)-cran40/" \
  && apt-get update -y \
  && apt-get install -y r-base r-base-dev r-recommended


RUN R --version

# Install R packages
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('BiocManager', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "BiocManager::install(c('multtest', 'S4Vectors','scran','scater','SummarizedExperiment', 'SingleCellExperiment', 'edgeR','MAST', 'DESeq2', 'BiocGenerics', 'GenomicRanges', 'IRanges', 'rtracklayer', 'monocle', 'Biobase', 'limma', 'glmGamPoi'))"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('remotes', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('SeuratObject', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('Seurat', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "BiocManager::install(c('scater','scDblFinder'))"

# add extra python packages
RUN pip install scikit-image papermill
RUN pip install anndata2ri
RUN pip install pertpy[de] rpy2
RUN pip install scib-metrics

RUN Rscript --no-echo --no-restore --no-save -e "remotes::install_version('Matrix', repos='https://cloud.r-project.org', version = '1.6.4')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('SeuratObject', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('Seurat', repos='https://cloud.r-project.org')"
RUN apt-get update -y && apt-get install -y libharfbuzz-dev  libfribidi-dev
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('textshaping', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('ragg', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "install.packages('ggrastr', repos='https://cloud.r-project.org')"
RUN Rscript --no-echo --no-restore --no-save -e "BiocManager::install(c('scater','scDblFinder'))"





