FROM continuumio/miniconda3


LABEL base.image="continuumio/miniconda3"
LABEL dockerfile.version="1"
LABEL maintainer="Alexandra Pancikova"
LABEL maintainer.email="alexandra.pancikova@kuleuven.be"


ADD requirements.txt /tmp/requirements.txt
RUN conda config --add channels conda-forge
RUN conda config --add channels pytorch
RUN conda config --add channels nvidia
RUN conda config --add channels bioconda
RUN conda config --add channels epi2melabs

RUN conda env create -f /tmp/requirements.txt --name scanpy

# Install additional packages
RUN  pip install sc-toolbox numpy-groupies

# Activate the environment and make it default
SHELL ["conda", "run", "-n", "scanpy", "/bin/bash", "-c"]
RUN echo "source activate scanpy" >> ~/.bashrc



# Set the default command to activate the environment and run bash
CMD ["bash", "-c", "source activate scanpy && /bin/bash"]
