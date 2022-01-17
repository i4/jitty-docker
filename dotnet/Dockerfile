FROM ubuntu:focal

ENV DEBIAN_FRONTEND=noninteractive
RUN \
	ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime \
	&& apt-get update -qq \
	&& apt install --yes -qq \
		autoconf \
		automake \
		bison \
		build-essential \
		clang-9 \
		cmake \
		curl \
		flex \
		gettext \
		git \
		libicu-dev \
		libkrb5-dev \
		liblldb-6.0-dev \
		liblttng-ust-dev \
		libssl-dev \
		libtool \
		libunwind8 \
		libunwind8-dev \
		lldb-6.0 \
		llvm-9 \
		locales \
		wget \
		zlib1g-dev \
	&& locale-gen en_US.UTF-8
RUN git clone https://github.com/dotnet/runtime.git /dotnet-bld && git -C /dotnet-bld checkout v5.0.0
RUN /dotnet-bld/build.sh clr -rc release

FROM mcr.microsoft.com/dotnet/runtime:5.0
COPY --from=0 /dotnet-bld/artifacts/bin/coreclr/Linux.x64.Release /ilasm
ENV DEBIAN_FRONTEND=noninteractive
ENV PATH="/ilasm:${PATH}"
RUN apt-get update -qq \
	&& apt install --yes -qq \
	binutils \
	gcc \
	make
