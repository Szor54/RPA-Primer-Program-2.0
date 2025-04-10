# Use the official Ubuntu base image
FROM ubuntu:latest

# Set environment variables to avoid user interaction during installations
ENV DEBIAN_FRONTEND=noninteractive

# Install essential tools
RUN apt-get update && apt-get install -y \
    nano \
    wget \
    curl \
    git \
    python3 \
    python3-pip \
    && rm -rf /var/lib/apt/lists/*
# Install pip packages globally
RUN pip3 install --no-cache-dir --break-system-packages \
    pandas \
    numpy

    
# Set the working directory
WORKDIR /usr/src/app

# Keep the container running
CMD ["tail", "-f", "/dev/null"]