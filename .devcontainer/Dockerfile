FROM python:3.8.20-bullseye

# Install apt packages
RUN apt-get update && apt-get install -y \
    git \
    wget \
    gnupg2 \
    ca-certificates \
    build-essential \
    gcc \
    g++ \
    make \
    tmux

# Install CUDA Toolkit
RUN wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
RUN sh cuda_11.8.0_520.61.05_linux.run --silent --toolkit --override && \
    rm cuda_11.8.0_520.61.05_linux.run

# Set CUDA environment variables
ENV CUDA_HOME=/usr/local/cuda-11.8
ENV PATH=${CUDA_HOME}/bin:$PATH
ENV LD_LIBRARY_PATH=${CUDA_HOME}/lib64:$LD_LIBRARY_PATH

# Install Python dependencies
RUN pip install --no-cache-dir --upgrade \
    pip==25.0.1 \
    setuptools==75.3.0 \
    setuptools-scm==8.2.0

RUN pip install --no-cache-dir \
    torch==2.1.0+cu118 \
    torchvision==0.16.0+cu118 --index-url https://download.pytorch.org/whl/cu118

RUN pip install --no-cache-dir \
    tensorboardX==2.6.2.2 \
    matplotlib==3.7.5 \
    numpy==1.24.1 \
    apex==0.9.10.dev0 \
    captum==0.7.0
