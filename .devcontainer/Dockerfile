FROM mcr.microsoft.com/devcontainers/java:21-bookworm

# Partly from
# https://github.com/microsoft/vscode-dev-containers/blob/main/containers/java/.devcontainer/Dockerfile
# https://github.com/dev-container/java/blob/master/.devcontainer/Dockerfile

# This Dockerfile adds a non-root user with sudo access. Use the "remoteUser"
# property in devcontainer.json to use it. On Linux, the container user's GID/UIDs
# will be updated to match your local UID/GID (when using the dockerFile property).
# See https://aka.ms/vscode-remote/containers/non-root-user for details.
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ENV DEBIAN_FRONTEND=noninteractive

#  将 /etc/apt/sources.list 文件中 Debian 默认的源地址 http://deb.debian.org/ 替换为镜像地址
RUN cat <<EOF > /etc/apt/sources.list
deb https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm main non-free non-free-firmware contrib

deb https://mirrors.aliyun.com/debian-security/ bookworm-security main
deb-src https://mirrors.aliyun.com/debian-security/ bookworm-security main

deb https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm-updates main non-free non-free-firmware contrib

deb https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
deb-src https://mirrors.aliyun.com/debian/ bookworm-backports main non-free non-free-firmware contrib
EOF
RUN rm -rf /etc/apt/sources.list.d && apt-get update;

RUN set -ex; \ 
    apt-get update; \
    apt-get install -y  --no-install-recommends \
        zip \
        unzip \
        bash-completion \
        build-essential \
        htop \
        jq \
        less \
        locales \
        man-db \
        software-properties-common \
        sudo \
        time \
        vim \
        multitail \
        lsof \
        openssh-client iproute2 lsb-release;

ENV DEBIAN_FRONTEND=dialog

COPY maven-settings.xml /home/vscode/.m2/settings.xml
RUN chmod 666 /home/vscode/.m2/settings.xml