# https://github.com/devcontainers/images/tree/main/src/javascript-node
FROM mcr.microsoft.com/devcontainers/javascript-node:18

# Add Base Debian Sources Repository
COPY ./sources.list /etc/apt/sources.list

# Update System and Install Packages non interactive
RUN export DEBIAN_FRONTEND=noninteractive \
    && apt-get update -y \
    && apt-get upgrade -y --no-install-recommends \
    && apt-get install -y --no-install-recommends \
        apt-transport-https \
        bat \
        ca-certificates \
        curl \
        fzf \
        gnupg \
        git \
        jq \
        nano \
        nginx \
        ripgrep \
        ssl-cert \
        stow \
        tmux \
        vim

# Install Google Chrome
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
    && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
    && apt-get update -y \
    && apt-get -y install google-chrome-stable

# Install Delta Pager
RUN wget https://github.com/dandavison/delta/releases/download/0.16.5/git-delta_0.16.5_amd64.deb \
    && dpkg -i git-delta_0.16.5_amd64.deb \
    && rm git-delta_0.16.5_amd64.deb

# Install Code Mini Map
RUN wget https://github.com/wfxr/code-minimap/releases/download/v0.6.4/code-minimap-musl_0.6.4_amd64.deb \
    && dpkg -i code-minimap-musl_0.6.4_amd64.deb \
    && rm code-minimap-musl_0.6.4_amd64.deb

# Install Git LFS
RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash \
    && apt-get update -y \
    && apt-get -y install git-lfs

# Cleanup Image
RUN apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*
