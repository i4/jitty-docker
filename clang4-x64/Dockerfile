FROM ubuntu:bionic

ENV CLANG_VERSION=4.0
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq \
	&& apt-get install --yes -qq \
		clang-${CLANG_VERSION} \
		cppcheck \
		expect \
		gcc \
		genisoimage \
		isolinux \
		libc6-dev \
		libc6-dev-i386 \
		llvm-${CLANG_VERSION} \
		make \
		qemu-system-x86 \
		sparse \
		telnet \
		wget
