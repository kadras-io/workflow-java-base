FROM ubuntu:22.04

ARG USER_UID="1000"
ARG USER_GID="1000"
ARG USER_NAME="workflow"

RUN groupadd -g $USER_GID $USER_NAME && \
	useradd -m -g $USER_GID -u $USER_UID $USER_NAME

RUN apt-get update && \
	apt-get install -y zip unzip curl && \
	rm -rf /var/lib/apt/lists/* && \
	rm -rf /tmp/*

USER $USER_UID:$USER_GID

RUN curl -s "https://get.sdkman.io" | bash

RUN bash -c "source $HOME/.sdkman/bin/sdkman-init.sh && \
  yes | sdk install java 11.0.19-tem && \
  yes | sdk install java 17.0.7-tem && \
  yes | sdk install java 20-tem && \
  sdk default java 17.0.7-tem && \
  rm -rf $HOME/.sdkman/archives/* && \
  rm -rf $HOME/.sdkman/tmp/*"
