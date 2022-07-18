# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.238.1/containers/ubuntu/.devcontainer/base.Dockerfile

# [Choice] Ubuntu version (use ubuntu-22.04 or ubuntu-18.04 on local arm64/Apple Silicon): ubuntu-22.04, ubuntu-20.04, ubuntu-18.04
ARG VARIANT="jammy"
FROM mcr.microsoft.com/vscode/devcontainers/base:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends jq curl shellcheck file \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# release code may have bugs so fetch the latest release
# https://raw.githubusercontent.com/wimpysworld/deb-get/0.3.1/deb-get


SHELL ["/bin/bash", "-o", "pipefail", "-c"]
RUN curl -sL https://raw.githubusercontent.com/wimpysworld/deb-get/$(wget -q https://api.github.com/repos/wimpysworld/deb-get/releases -O -  |grep "tag_name" | head -n1 | cut -d'"' -f4)/deb-get | sudo -E bash -s install deb-get