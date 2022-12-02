FROM mcr.microsoft.com/devcontainers/universal:2-linux

# Install Kafka
ARG KAFKA_VERSION=2.13-3.3.1
ADD https://downloads.apache.org/kafka/3.3.1/kafka_$KAFKA_VERSION.tgz .
ADD https://downloads.apache.org/kafka/3.3.1/kafka_$KAFKA_VERSION.tgz.sha512 .
RUN echo "$(cat \
    "kafka_$KAFKA_VERSION.tgz.sha512" | \
    tr '[:upper:]\r\n' '[:lower:]  ' | \
    sed -e "s/kafka_$KAFKA_VERSION.tgz://" -e 's/\s//g' \
    ) kafka_$KAFKA_VERSION.tgz" | sha512sum -c && \
    tar xzf kafka_$KAFKA_VERSION.tgz && \
    rm kafka_$KAFKA_VERSION.tgz*
ENV PATH=/kafka_2.13-3.3.1/bin:$PATH

# Install kcat
ARG DEBIAN_FRONTEND=noninteractive
RUN --mount=type=cache,target=/var/cache/apt,sharing=private \
    --mount=type=cache,target=/var/lib/apt/lists,sharing=private \
    sudo apt-get update && \
    sudo apt-get install -y --no-install-recommends \
    clang \
    cmake \
    jq \
    kafkacat \
    lld \
    llvm \
    protobuf-compiler \
    zstd

# Install init scripts
ADD *.sh /usr/local/bin/

# Install cargo bins
COPY --from=ghcr.io/bitskico/rust-sdk /usr/local/rust-sdk /usr/local/
ENV PATH=/usr/local/rust-sdk/bin:$PATH
