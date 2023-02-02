# for source of the base container see https://github.com/jupyter/docker-stacks/tree/master/base-notebook
ARG BASE_CONTAINER=jupyter/minimal-notebook
FROM $BASE_CONTAINER

# change in date forces rebuild of the image
ENV REFRESHED_AT 2023.02.02

#RUN echo 'Acquire::http { Proxy "http://172.18.0.1:3142"; };' >> /etc/apt/apt.conf.d/01proxy

USER root

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update --yes && \
    apt-get upgrade --yes && \
    apt-get install --yes --no-install-recommends build-essential git aspell aspell-en aspell-pl

#RUN wget -q --show-progress https://github.com/valentjn/ltex-ls/releases/download/15.2.0/ltex-ls-15.2.0-linux-x64.tar.gz -P /tmp && tar xf /tmp/ltex-ls-15.2.0-linux-x64.tar.gz --strip-components=2 -C /usr --exclude={*.md,*.xml} && rm /tmp/ltex-ls*

RUN git clone https://github.com/mitshell/CryptoMobile
WORKDIR "CryptoMobile"
RUN python setup.py install && cd .. && rm -rf CryptoMobile

USER $NB_UID
WORKDIR "/home/${NB_USER}/"

RUN pip install pycryptodome
RUN pip install eciespy

