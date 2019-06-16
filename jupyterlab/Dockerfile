FROM jupyter/datascience-notebook
MAINTAINER Suguru Ohki
USER root

RUN set -x && \
    apt-get update \
    && apt-get install -y \
    mecab \
    libmecab-dev \
    mecab-ipadic-utf8 \
    git \
    make \
    curl \
    xz-utils \
    file \
    sudo \
    wget \
    vim \
    software-properties-common \
    python-pip \
    mysql-client

RUN git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git\
    && cd mecab-ipadic-neologd \
    && bin/install-mecab-ipadic-neologd -n -y

WORKDIR code
# ADD requirements.txt /code/
COPY . .
RUN pwd && ls -a
# RUN ls -a ../
RUN sudo pip install --upgrade pip && pip install -r ./jupyterlab/requirements.txt
RUN jupyter serverextension enable --py jupyterlab
