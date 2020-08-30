FROM continuumio/miniconda3:4.7.12

WORKDIR /root

RUN apt-get update -qy && apt-get install -qy \
    procps \
    htop \
    zip \
    unzip \
    vim \
    gnupg \
    texlive-xetex \
    software-properties-common \
    protobuf-compiler \
    build-essential \
    >/dev/null 2>&1

COPY conda_init.yml ./conda.yml
#COPY conda_lock.yml ./conda.yml

RUN conda env update -n base -f conda.yml

# https://github.com/axelfahy/jupyterlab-vim
RUN jupyter labextension install @axlair/jupyterlab_vim

# Nvidia Runtime
ENV NVIDIA_VISIBLE_DEVICES=all
ENV NVIDIA_DRIVER_CAPABILITIES=compute,utility
ENV NVIDIA_REQUIRE_CUDA="cuda>=10.0 brand=tesla,driver>=384,driver<385 brand=tesla,driver>=410,driver<411"