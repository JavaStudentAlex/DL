FROM tensorflow/tensorflow:2.14.0-gpu

ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=off \
    PIP_DISABLE_PIP_VERSION_CHECK=1 \
    PIP_DEFAULT_TIMEOUT=100 \
    C_FORCE_ROOT=true \
    DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y ca-certificates software-properties-common build-essential git \
                          texlive texlive-latex-extra texlive-xetex pandoc \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -u 1317 -d /home/jovyan -s /bin/bash jovyan
RUN mkdir -p /home/jovyan && chown -R jovyan:jovyan /home/jovyan
WORKDIR /home/jovyan

RUN mkdir -p /ray && chown -R jovyan:jovyan /ray

RUN chmod 777 /etc
RUN chmod 777 /usr/bin/pandoc

COPY ./start.sh /usr/local/bin/start.sh
RUN chmod 777 /usr/local/bin/start.sh

RUN pip install --upgrade pip setuptools
RUN pip install "ray[all]" \
    "flaml[blendsearch]" \
    git+https://github.com/optuna/optuna \
    tensorrt \
    async-timeout \
    numpy \
    pandas \
    scikit-learn \
    tqdm \
    matplotlib \
    seaborn \
    plotly \
    tqdm \
    jupyterlab \
    ipywidgets \
    ydata-profiling \
    pandoc


USER jovyan