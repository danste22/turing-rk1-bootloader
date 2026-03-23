FROM gcc:15.2.0

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y bison curl make flex python3-pyelftools python3-setuptools python3-dev swig \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /workspace
