FROM nvidia/cuda:9.1-cudnn7-devel

RUN apt-get -qq update &&  \
    apt-get -qq install --assume-yes build-essential git wget pkg-config locales \
      gcc g++ gfortran libopenblas-dev && \
    rm -rf /var/lib/apt/lists/*

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && locale-gen
ENV LC_ALL en_US.utf8

RUN wget --quiet https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh

RUN /opt/conda/bin/conda install -q -y conda numpy scipy pip pillow cython && \
  /opt/conda/bin/python3.6 -m pip install --upgrade pip && \
  /opt/conda/bin/python3.6 -m pip install --upgrade --no-deps https://github.com/Theano/Theano/archive/master.zip && \
  /opt/conda/bin/python3.6 -m pip install --upgrade --no-deps https://github.com/Lasagne/Lasagne/archive/master.zip
