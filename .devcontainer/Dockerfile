# Custom Docker image for building U-Boot

FROM ubuntu:20.04

# Set environment variables
environment_variables:
  DEBIAN_FRONTEND=noninteractive

# Install necessary dependencies
RUN apt-get update && \  
    apt-get install -y \  
    build-essential \  
    git \  
    python3 \  
    gcc \  
    g++ \  
    make \  
    bison \  
    flex \  
    libssl-dev \  
    pkg-config \  
    libc6-dev \  
    libncurses5-dev \  
    libncursesw5-dev \  
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /workspace

