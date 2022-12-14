FROM mcr.microsoft.com/devcontainers/universal:2-linux

# Install CockroachDB
ADD https://binaries.cockroachdb.com/cockroach-v22.1.11.linux-amd64.tgz .
RUN tar -xzf cockroach-v22.1.11.linux-amd64.tgz && \
    sudo cp -i cockroach-v22.1.11.linux-amd64/cockroach /usr/local/bin/ && \
    rm -rf cockroach-v22.1.11.linux-amd64*

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
