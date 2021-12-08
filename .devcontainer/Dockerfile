ARG NODE_VERSION=12
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${NODE_VERSION}

ARG VARIANT=hugo
ARG VERSION=latest

RUN apt-get update && apt-get install -y ca-certificates openssl git curl && \
    rm -rf /var/lib/apt/lists/* && \
    case ${VERSION} in \
    latest) \
    export VERSION=$(curl -s https://api.github.com/repos/gohugoio/hugo/releases/latest | grep "tag_name" | awk '{print substr($2, 3, length($2)-4)}') ;;\
    esac && \
    echo ${VERSION} && \
    wget -O ${VERSION}.tar.gz https://github.com/gohugoio/hugo/releases/download/v${VERSION}/${VARIANT}_${VERSION}_Linux-64bit.tar.gz && \
    tar xf ${VERSION}.tar.gz && \
    mv hugo /usr/bin/hugo

EXPOSE 1313

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive
RUN sudo -u node npm install -g yarn
