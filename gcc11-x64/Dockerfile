FROM ubuntu:impish

ENV GCC_VERSION=11
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq  && apt-get install --yes -qq \
		make libc6-dev \
		binutils flex bison \
		gcc-${GCC_VERSION} gcc \
		g++-${GCC_VERSION} g++
