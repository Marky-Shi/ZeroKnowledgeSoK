FROM ubuntu:22.04 as base

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get update && apt-get install \
    -y build-essential cmake git libgmp3-dev libprocps-dev libboost-all-dev libssl-dev libsodium-dev nano wget

RUN git clone https://github.com/KULeuven-COSIC/Limbo.git

WORKDIR Limbo

# COPY limbo_instances.cpp /Limbo/limbo_instances.cpp

RUN mkdir build

WORKDIR build

RUN cmake .. && make

RUN wget https://nigelsmart.github.io/MPC-Circuits/sha256.txt && ./bench sha256.txt 0

# COPY matmul64.txt .
# RUN ./bench matmul64.txt 0