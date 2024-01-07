FROM --platform=linux/amd64 ruby:3.2.2-slim-bookworm

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID
ARG MIHARI_VERSION=7.1.0

# create the user
RUN groupadd --gid $USER_GID $USERNAME && \
  useradd --uid $USER_UID --gid $USER_GID -m $USERNAME

# setup requirements
RUN apt update && \
  apt install -y --no-install-recommends build-essential sudo curl wget jq vim git unzip sqlite3 && \
  # cleanup
  apt-get autoremove -y && \
  apt-get clean -y && \
  rm -rf /var/lib/apt/lists/* && \
  # make it possible to use sudo
  echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
  chmod 0440 /etc/sudoers.d/$USERNAME

# prevent installing document
RUN echo 'gem: --no-document' >> /usr/local/etc/gemrc

# install Nuclei
RUN wget https://github.com/projectdiscovery/nuclei/releases/download/v3.1.3/nuclei_3.1.3_linux_amd64.zip && \
  unzip nuclei_3.1.3_linux_amd64.zip && \
  mv nuclei /usr/local/bin && \
  rm nuclei_3.1.3_linux_amd64.zip

USER $USERNAME

# install Mihari
RUN gem install mihari -v $MIHARI_VERSION

# install Nuclei templates
RUN nuclei

