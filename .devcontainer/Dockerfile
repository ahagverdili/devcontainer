FROM debian:stable-slim

ENV LANG=C.UTF-8

RUN export DEBIAN_FRONTEND=noninteractive && \
    apt-get update -y && \
    apt-get upgrade -y && \
    apt-get autoremove -y && \
    apt-get -y install --no-install-recommends \
        clangd \
        fish \
        cmake \
        build-essential \
        git \
        curl \
        ninja-build \
        ccache \
        qt6-base-dev \
        qt6-declarative-dev \
        qt6-wayland \
        libxkbcommon-dev \
        libxcb-cursor0 \
        libxcb-xfixes0-dev \
        libqt6quickcontrols2-6 \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN useradd -m vscode
RUN groupadd -g 992 render && usermod -aG video,render vscode

RUN apt-get update && apt-get install -y sudo \
    && echo "vscode ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

RUN chsh -s "$(which fish)" vscode
