# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.231.5/containers/typescript-node/.devcontainer/base.Dockerfile

# Node.js version (use -bullseye variants on local arm64/Apple Silicon): 16, 14, 12, 16-bullseye, 14-bullseye, 12-bullseye, 16-buster, 14-buster, 12-buster
ARG VARIANT="14"
FROM mcr.microsoft.com/vscode/devcontainers/typescript-node:0-${VARIANT}

# Theia dependencies
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
     && apt-get -y install --no-install-recommends \
     make \
     gcc \
     pkg-config \
     build-essential \
     python3.10 \
     python3-pip \
     software-properties-common \
     libx11-dev \
     libxkbfile-dev \
     libsecret-1-dev \
     libssl-dev

RUN python -m pip install --upgrade pip
RUN pip install torch torchvision torchaudio --extra-index-url https://download.pytorch.org/whl/cpu
RUN pip install torch-scatter torch-sparse torch-cluster torch-spline-conv torch-geometric -f https://data.pyg.org/whl/torch-1.12.0+cpu.html
RUN pip install numpy random2 neomodel
#RUN pip install 'python-language-server[all]'

# install code generator for vs code, theia extensions, theia plugins
RUN npm install -g yo code generator-theia-extension @theia/generator-plugin

USER node

EXPOSE 3000