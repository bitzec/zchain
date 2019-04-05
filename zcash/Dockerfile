FROM ubuntu:16.04

RUN apt-get update -q && apt-get -qy install \
      build-essential pkg-config libc6-dev m4 g++-multilib \
      autoconf libtool ncurses-dev unzip git python \
      zlib1g-dev wget bsdmainutils automake

WORKDIR /root/
RUN git clone https://github.com/bitzec/bitzec.git
WORKDIR /root/bitzec/
RUN git fetch --tags
RUN git checkout v1.0.14
RUN ./zcutil/fetch-params.sh

RUN apt-get -y install curl

RUN ./zcutil/build.sh -j$(nproc)

CMD ["/root/bitzec/src/bitzecd", "-logips"]
