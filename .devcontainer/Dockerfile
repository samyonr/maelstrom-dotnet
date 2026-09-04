FROM mcr.microsoft.com/dotnet/sdk:10.0-noble

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        bzip2 \
        gnuplot \
        graphviz \
        openjdk-25-jdk-headless \
        ruby \
    && rm -rf /var/lib/apt/lists/*

ARG MAELSTROM_VERSION=0.2.4

RUN mkdir -p /opt/maelstrom \
    && curl --fail --show-error --location \
        "https://github.com/jepsen-io/maelstrom/releases/download/v${MAELSTROM_VERSION}/maelstrom.tar.bz2" \
        --output /tmp/maelstrom.tar.bz2 \
    && tar -xjf /tmp/maelstrom.tar.bz2 \
        -C /opt/maelstrom \
        --strip-components=1 \
    && rm /tmp/maelstrom.tar.bz2 \
    && ln -s /opt/maelstrom/maelstrom /usr/local/bin/maelstrom