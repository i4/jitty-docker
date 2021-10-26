FROM ubuntu:latest

ENV DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime \
	&& apt-get update \
	&& apt install --yes -qq \
		git wget build-essential \
		cmake llvm-9 clang-9 curl lldb-6.0 liblldb-6.0-dev libunwind8 libunwind8-dev gettext libicu-dev liblttng-ust-dev libssl-dev libkrb5-dev zlib1g-dev \
		locales autoconf automake \
		libtool \
	&& locale-gen en_US.UTF-8 \
	&& git clone https://github.com/dotnet/runtime.git /dotnet-runtime

WORKDIR /dotnet-runtime

RUN git checkout v5.0.0 && ./build.sh

ENV PATH="/dotnet-runtime/artifacts/bin/coreclr/Linux.x64.Debug:${PATH}"
ENV PATH="/dotnet-runtime/.dotnet:${PATH}"
