FROM ubuntu:22.04

# Install dependencies
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y \
    python3 \
    python3-pip \
    build-essential \
    wget \
    git \
    bzip2 \
    ca-certificates \
    zlib1g-dev \
    html2text

# Set alias for python3
RUN ln -s /usr/bin/python3 /usr/bin/python

# Create bin dir for installed tools
RUN mkdir -p /opt/bin
ENV PATH="/opt/bin:${PATH}"

# Install kma (LRE-Finder dependency)
RUN git clone https://bitbucket.org/genomicepidemiology/kma.git && \
    cd kma && \
    make && \
    mv kma /opt/bin/

# Install LRE-Finder
RUN git clone https://bitbucket.org/genomicepidemiology/lre-finder.git && \
    cd lre-finder && \
    make && \
    tar -xvzf elmDB.tar.gz && \
    kma index -i elmDB/elm.fsa -o elmDB/elm && \
    cp LRE-Finder.py /opt/bin/ && \
    cp getGene /opt/bin/

ENV PATH="/opt/bin:$PATH"