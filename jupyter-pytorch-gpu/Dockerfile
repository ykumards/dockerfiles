FROM pytorch/pytorch
MAINTAINER "Yogesh Kumar"

RUN apt-get update && apt-get install -y wget ca-certificates \
    git curl vim python3-dev python3-pip \
    libfreetype6-dev libpng12-dev

ENV PYTHON_VERSION=3.6

RUN curl -o ~/miniconda.sh -O  https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh  && \
     chmod +x ~/miniconda.sh && \
     ~/miniconda.sh -b -p /opt/conda && \     
     rm ~/miniconda.sh && \
#     /opt/conda/bin/conda install conda-build && \
     /opt/conda/bin/conda create -y --name pytorch-py$PYTHON_VERSION python=$PYTHON_VERSION numpy pyyaml scipy ipython mkl&& \
     /opt/conda/bin/conda clean -ya 
ENV PATH /opt/conda/envs/pytorch-py$PYTHON_VERSION/bin:$PATH
RUN conda install --name pytorch-py$PYTHON_VERSION -c soumith magma-cuda80

RUN pip3 install --upgrade pip
RUN pip3 install numpy pandas sklearn matplotlib seaborn jupyter
RUN pip3 install torchvision

RUN ["mkdir", "notebooks"]
COPY jupyter_notebook_config.py /root/.jupyter/
COPY run_jupyter.sh /

# Jupyter port
EXPOSE 8888

# Store notebooks in this mounted directory
VOLUME /notebooks

CMD ["/run_jupyter.sh"]