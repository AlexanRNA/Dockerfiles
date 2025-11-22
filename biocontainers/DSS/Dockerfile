FROM quay.io/biocontainers/bioconductor-dss:2.54.0--r44h3df3fcb_0

RUN pip install jupyter_client 

RUN R -e "install.packages(c('IRkernel', 'ggplot2'), repos='https://cloud.r-project.org')"


