FROM rootproject/root-ubuntu16

USER root
RUN apt-get update && apt-get install -y liblz4-dev cmake && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp/
RUN git clone https://github.com/JeffersonLab/hipo_tools.git \
    && mkdir -p hipo_tools/build && cd hipo_tools/build \
    && cmake .. \
    && make -j$(nproc) \
    && make install \
    && rm -rf /tmp/*
