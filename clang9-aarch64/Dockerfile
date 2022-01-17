FROM ubuntu:focal

ENV CLANG_VERSION=9
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq \
	&& apt-get install --yes -qq \
		clang-${CLANG_VERSION} \
		cppcheck \
		expect \
		gcc \
		gcc-9-aarch64-linux-gnu \
		gcc-aarch64-linux-gnu \
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

# gcc-arch64-linux-gnu works with clang5, 6, 7, 8 and 9
