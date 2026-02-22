FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install dependencies
RUN apt-get update && apt-get install -y \
    curl \
    git \
    sudo \
    ca-certificates \
    && rm -rf /var/lib/apt/lists/*

# Install code-server
RUN curl -fsSL https://code-server.dev/install.sh | sh

# Create workspace
RUN mkdir -p /workspace
WORKDIR /workspace

# Render uses dynamic PORT
ENV PORT=10000

EXPOSE 10000

# Start VS Code server (no auth for simplicity)
CMD code-server --bind-addr 0.0.0.0:$PORT --auth none
