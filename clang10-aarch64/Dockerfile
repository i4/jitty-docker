FROM ubuntu:focal

ENV CLANG_VERSION=10
ENV DEBIAN_FRONTEND=noninteractive

RUN \
	apt-get update -qq  && apt-get install --yes -q \
	qemu-system-x86 expect wget telnet make \
	gcc-7-aarch64-linux-gnu gcc-aarch64-linux-gnu \
	isolinux make gcc libc6-dev libc6-dev-i386 genisoimage sparse \
	clang-${CLANG_VERSION} llvm-${CLANG_VERSION}

# gcc-arch64-linux-gnu works with clang5, 6, 7, 8 and 9
