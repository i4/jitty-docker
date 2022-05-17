FROM mcr.microsoft.com/dotnet/runtime:5.0

ENV DEBIAN_FRONTEND=noninteractive
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1
RUN \
	ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime \
	&& apt-get update -qq \
	&& apt install --yes -qq \
		clang \
		cmake \
		git \
		locales \
		python3 \
		wget \
	&& echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen && update-locale LANG=en_US.UTF-8 \
	&& apt install --yes -qq \
		libicu-dev \
		liblttng-ust-dev
RUN git clone -b v5.0.0 --depth 1 https://github.com/dotnet/runtime.git /dotnet-bld && git -C /dotnet-bld checkout v5.0.0
RUN /dotnet-bld/build.sh clr -rc release

FROM mcr.microsoft.com/dotnet/runtime:5.0
COPY --from=0 /dotnet-bld/artifacts/bin/coreclr/Linux.x64.Release /ilasm
ENV DEBIAN_FRONTEND=noninteractive
ENV DOTNET_CLI_TELEMETRY_OPTOUT=1
ENV PATH="/ilasm:${PATH}"
RUN apt-get update -qq \
	&& apt install --yes -qq locales \
	&& echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen && locale-gen && update-locale LANG=en_US.UTF-8 \
	&& apt install --yes -qq \
		libicu-dev \
		liblttng-ust-dev \
		make libc6-dev \
		binutils flex bison
