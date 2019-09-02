FROM nvidia/cuda:10.0-cudnn7-devel-ubuntu16.04

MAINTAINER team@gnes.ai

ARG TENSORFLOW_VERSION=1.14.0
ARG TORCH_VERSION=1.1.0
ARG TORCH_VISION_VERSION=0.3.0

ENV LANG=C.UTF-8

RUN apt-get update -y && apt-get install -y --no-install-recommends \
    build-essential \
    vim \
    git \
    wget \
    curl \
    cmake \
    unzip \
    gcc \
    g++ \
    automake \
    software-properties-common \
    libzmq5 \
    libblas-dev \
    liblapack-dev \
    libpcre3 \
    libpcre3-dev \
    bison \
    byacc \
    ffmpeg \
    libsm6 libxext6 libxrender-dev \
    && apt-get clean

# Install python-3.6
RUN add-apt-repository -y ppa:jonathonf/python-3.6 \
    && apt-get update -y \
    && apt-get install -y python3.6 python3.6-dev \
    && ln -sfn /usr/bin/python3.6 /usr/local/bin/python \
    && ln -sfn /usr/bin/python3.6 /usr/bin/python3 \
    && curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python get-pip.py \
    && rm get-pip.py \
    && apt-get autoremove -y \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


# Install TensorFlow
RUN pip --no-cache-dir install tensorflow-gpu==${TENSORFLOW_VERSION}

# Install pytorch and torchvision
RUN pip --no-cache-dir install \
    https://download.pytorch.org/whl/cu100/torch-${TORCH_VERSION}-cp36-cp36m-linux_x86_64.whl
RUN pip --no-cache-dir install \
    https://download.pytorch.org/whl/cu100/torchvision-${TORCH_VISION_VERSION}-cp36-cp36m-linux_x86_64.whl


# Install faiss
# Need SWIG >= 3.0.8
RUN cd /tmp/ \
    && wget -q https://github.com/swig/swig/archive/rel-3.0.12.tar.gz \
    && tar zxf rel-3.0.12.tar.gz; rm rel-3.0.12.tar.gz && cd swig-rel-3.0.12 \
    && ./autogen.sh; ./configure >/dev/null \
    && make >/dev/null \
    && make install >/dev/null \
    && cd .. && rm -rf swig-rel-3.0.12

# install faiss from source
RUN wget -q https://github.com/facebookresearch/faiss/archive/v1.5.3.tar.gz \
    && tar zxf v1.5.3.tar.gz; rm v1.5.3.tar.gz && cd faiss-1.5.3 \
    && ./configure --with-cuda=/usr/local/cuda-10.0 \
    && make -j 10 \
    && cd python && make \
    && pip --no-cache-dir install . \
    && cd .. && rm -rf faiss-1.5.3 \
    && rm -rf /tmp/*
