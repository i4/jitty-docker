FROM ubuntu:focal

ENV DEBIAN_FRONTEND=noninteractive
RUN ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime \
	&& apt-get update \
	&& apt install --yes -qq \
		git wget build-essential \
		cmake llvm-9 clang-9 curl lldb-6.0 liblldb-6.0-dev libunwind8 libunwind8-dev gettext libicu-dev liblttng-ust-dev libssl-dev libkrb5-dev zlib1g-dev \
		flex bison \
		locales autoconf automake \
		libtool \
	&& locale-gen en_US.UTF-8
RUN git clone https://github.com/dotnet/runtime.git /dotnet-bld && git -C /dotnet-bld checkout v5.0.0
RUN /dotnet-bld/build.sh clr -rc release

FROM mcr.microsoft.com/dotnet/runtime:5.0
COPY --from=0 /dotnet-bld/artifacts/bin/coreclr/Linux.x64.Release /ilasm
ENV DEBIAN_FRONTEND=noninteractive
ENV PATH="/ilasm:${PATH}"
RUN apt-get update && apt install --yes -qq make binutils gcc
