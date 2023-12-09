FROM nvidia/cuda:11.6.1-runtime-ubuntu20.04

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=off \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_DEFAULT_TIMEOUT=100 \
    C_FORCE_ROOT=true \
    DEBIAN_FRONTEND=noninteractive

RUN apt-get update  \
    && apt-get upgrade -y \
    && apt-get install -y ca-certificates software-properties-common build-essential \
    && add-apt-repository ppa:deadsnakes/ppa \
    && apt-get update \
    && apt-get install -y python3.10 python3-pip \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -u 1317 -d /home/jovyan -s /bin/bash jovyan
RUN mkdir -p /home/jovyan && chown -R jovyan:jovyan /home/jovyan
WORKDIR /home/jovyan

RUN mkdir -p /ray && chown -R jovyan:jovyan /ray

RUN mkdir -p /usr/bin/pandoc && chmod 777 /usr/bin/pandoc
RUN chmod 777 /etc

COPY ./start.sh /usr/local/bin/start.sh
RUN chmod 777 /usr/local/bin/start.sh

RUN pip install --upgrade pip setuptools
RUN pip install tensorflow[and-cuda] \
    jupyterlab \
    ipywidgets

USER jovyan