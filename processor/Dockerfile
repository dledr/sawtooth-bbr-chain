FROM rust:1

RUN apt-get update && apt-get install -y \
        libprotobuf-dev \
        libprotoc-dev \
        libzmq3-dev \
        protobuf-compiler \
        unzip \
    && rm -rf /var/lib/apt/lists/*

ENV BBR_WS /opt/sawtooth-bbr-chain
WORKDIR $BBR_WS
RUN USER=root cargo new --bin processor

WORKDIR $BBR_WS/processor
COPY Cargo.toml Cargo.lock* ./
RUN cargo build

ENV PATH=$PATH:$BBR_WS/processor/target/debug/

ENTRYPOINT ["bbr-chain-tp"]