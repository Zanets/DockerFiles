FROM ubuntu:latest
MAINTAINER tsmh

RUN apt-get update \ 
    && apt-get upgrade -y \
    && apt-get install -y \
	vim \
	sudo \
	git \
	curl \
	mongodb \
	redis-server \
	tmux \
	default-jdk

RUN service mongodb start
RUN service redis-server start
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 8.4.0
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash \
    && . $NVM_DIR/nvm.sh \
    && nvm install $NODE_VERSION \
    && nvm use $NODE_VERSION

ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/v$NODE_VERSION/bin:$PATH

RUN mkdir /Pewss
WORKDIR /Pewss
RUN git clone https://github.com/darg20127/Pewss /Pewss
RUN npm install -g yarn \
    && yarn install

RUN mkdir Server/Secrets/TLS
COPY Secrets/TLS/* Server/Secrets/TLS
COPY Secrets/Config.json Server/Secrets/

EXPOSE 8081
 
RUN useradd -ms /bin/bash tsmh
RUN usermod -a -G sudo tsmh
RUN echo 'tsmh:tsmh' | chpasswd

USER tsmh
WORKDIR /home/tsmh

