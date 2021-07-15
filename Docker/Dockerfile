# v0.1
FROM ubuntu:20.04

# Use clang
ENV CC clang
ENV CXX clang++

# apt-get install packages
RUN apt-get update && \
apt-get install -y \
clang \
git \
python3-pip \
python3-venv \
wget \
&& apt-get autoremove -y

# Install cmake
RUN wget -O cmake.sh https://github.com/Kitware/CMake/releases/download/v3.20.5/cmake-3.20.5-Linux-x86_64.sh && sh ./cmake.sh --prefix=/usr/local --skip-license

# Python venv
ENV VIRTUAL_ENV=/usr/project/fprime-venv

RUN python3 -m venv $VIRTUAL_ENV

ENV PATH="$VIRTUAL_ENV/bin:$PATH"

# Set workdir
WORKDIR /usr/project

# Install fprime
RUN git clone https://github.com/nasa/fprime
RUN pip install --upgrade fprime-tools fprime-gds

# Change workdir
WORKDIR /usr/project/fprime

EXPOSE 5000
EXPOSE 50000
