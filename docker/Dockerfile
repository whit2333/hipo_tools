FROM rootproject/root-ubuntu16

USER root
RUN apt-get update && apt-get install -y liblz4-dev cmake && rm -rf /var/lib/apt/lists/*

#install latest cmake
RUN curl https://cmake.org/files/v3.9/cmake-3.9.6-Linux-x86_64.sh -o /tmp/cmake-3.9.6-Linux-x86_64.sh \
	&& mkdir /opt/cmake \
	&& sh /tmp/cmake-3.9.6-Linux-x86_64.sh --prefix=/opt/cmake --skip-license \
	&& ln -s /opt/cmake/bin/cmake /usr/local/bin/cmake \
	&& rm -rf /tmp/*

WORKDIR /tmp/
RUN git clone https://github.com/JeffersonLab/hipo_tools.git \
    && mkdir -p hipo_tools/build && cd hipo_tools/build \
    && cmake .. \
    && make -j$(nproc) \
    && make install \
    && rm -rf /tmp/*
