FROM ubuntu:24.10 as clang19-builder


ENV DEBIAN_FRONTEND=noninteractive

RUN apt update && apt install -y \
  default-jdk python3-dev python3-pip python3-pytest libzmq5-dev build-essential \
  clang-19 clang-tidy-19 libc++-19-dev libc++abi-19-dev libstdc++-14-dev \
  libsodium-dev libssl-dev openssl \
  cmake git wget swig mpich libboost-dev ca-certificates \
  && apt-get clean && rm -rf /var/lib/apt/lists/* \
  && ln -s /usr/bin/llvm-symbolizer-19 /usr/bin/llvm-symbolizer \
  && ln -s /usr/bin/clang++-19 /usr/bin/clang++ \
  && ln -s /usr/bin/clang-19 /usr/bin/clang \
  && ln -s /usr/bin/clang-tidy-19 /usr/bin/clang-tidy

ENV CC=/usr/bin/clang
ENV CXX=/usr/bin/clang++

LABEL maintainer="helicsdevelopers@helics.org"
LABEL date="2024-12-02"
