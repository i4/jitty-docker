FROM ubuntu:bionic

ENV CLANG_VERSION=8
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq \
	&& apt-get install --yes -qq \
		clang-${CLANG_VERSION} \
		clang-tidy-${CLANG_VERSION} \
		cppcheck \
		expect \
		gcc \
		genisoimage \
		grub-common \
		isolinux \
		libc6-dev \
		libc6-dev-i386 \
		llvm-${CLANG_VERSION} \
		make \
		qemu-system-x86 \
		sparse \
		telnet \
		xorriso \
		wget \
	&& update-alternatives --install /usr/bin/clang-tidy clang-tidy $(command -v clang-tidy-${CLANG_VERSION}) 90
