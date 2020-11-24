FROM ubuntu:xenial

ENV CLANG_VERSION=3.5
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq  && apt-get install --yes -qq \
	qemu-system-x86 expect wget telnet make \
	isolinux make gcc libc6-dev libc6-dev-i386 genisoimage sparse \
	clang-${CLANG_VERSION} llvm-${CLANG_VERSION}

