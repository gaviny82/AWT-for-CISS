# FROM pytorch/pytorch:2.1.2-cuda11.8-cudnn8-devel
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
    make

# Install CUDA Toolkit
RUN wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
RUN sh cuda_11.8.0_520.61.05_linux.run --silent --toolkit --override

# Install dependencies
RUN pip install --upgrade pip && pip install --no-cache-dir \
    torch==2.1.0+cu118 \
    torchvision==0.16.0+cu118 --index-url https://download.pytorch.org/whl/cu118

# Add NVIDIA package repository
# RUN wget https://developer.download.nvidia.com/compute/cuda/repos/debian10/x86_64/cuda-keyring_1.0-1_all.deb && \
#     dpkg -i cuda-keyring_1.0-1_all.deb && \
#     apt-get update && \
#     apt-get install -y cuda-toolkit-10-2 && \
#     rm -rf /var/lib/apt/lists/*

RUN pip install --no-cache-dir \
    tensorboardX \
    matplotlib \
    numpy \
    apex \
    captum
    # inplace-abn

# RUN pip install --no-cache-dir \
#     tensorboardX==1.8 \
#     matplotlib==3.3.1 \
#     numpy==1.17.2 \
#     apex==0.1 \
#     captum
#     inplace-abn


# Install apex
# RUN git clone https://github.com/NVIDIA/apex.git && \
#     cd apex && \
#     pip install -v --disable-pip-version-check --no-cache-dir --no-build-isolation --global-option="--cpp_ext" --global-option="--cuda_ext" ./ && \
#     cd .. && rm -rf apex
