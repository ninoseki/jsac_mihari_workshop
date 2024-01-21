FROM --platform=linux/amd64 ruby:3.3.0-slim-bookworm

ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

ARG MIHARI_VERSION=7.3.1
ARG NUCLEI_VERSION=3.1.5

# Setup requirements
RUN apt update && \
  apt install -y --no-install-recommends build-essential sudo curl wget jq vim git unzip sqlite3 whois && \
  apt-get autoremove -y && \
  apt-get clean -y && \
  rm -rf /var/lib/apt/lists/*

# Create user
RUN groupadd --gid $USER_GID $USERNAME && \
  useradd --uid $USER_UID --gid $USER_GID -m $USERNAME && \
  echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
  chmod 0440 /etc/sudoers.d/$USERNAME

# Prevent installing document
RUN echo 'gem: --no-document' >> /usr/local/etc/gemrc

# Install Nuclei
RUN wget https://github.com/projectdiscovery/nuclei/releases/download/v3.1.5/nuclei_${NUCLEI_VERSION}_linux_amd64.zip && \
  unzip nuclei_${NUCLEI_VERSION}_linux_amd64.zip && \
  mv nuclei /usr/local/bin && \
  rm nuclei_${NUCLEI_VERSION}_linux_amd64.zip

# Enable YJIT
ENV RUBY_YJIT_ENABLE=1

USER $USERNAME

# Install Mihari
RUN gem install mihari -v $MIHARI_VERSION

# Install Nuclei templates
RUN nuclei

