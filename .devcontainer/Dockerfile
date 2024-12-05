# Use Ubuntu 23.10 as the base image
FROM ubuntu:23.10

# Set working directory inside the container
WORKDIR /home/container_project

# Install required tools and dependencies
RUN apt update && apt install -y \
    git \
    cmake \
    gdb \
    build-essential \
    clang \
    clang-tidy \
    clang-format \
    gcc-doc \
    pkg-config \
    glibc-doc \
    tcpdump \
    tshark \
    && apt clean && rm -rf /var/lib/apt/lists/*

# Copy only necessary files for build
COPY CMakeLists.txt ./
COPY etc ./etc
COPY src ./src
COPY apps ./apps
COPY util ./util
COPY tests ./tests

# Configure and build the project
RUN cmake -S . -B ./build && cmake --build ./build

# Default command to keep the container running
CMD ["/bin/bash"]
