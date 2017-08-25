FROM ubuntu:latest
MAINTAINER tsmh

RUN apt-get update \ 
    && apt-get upgrade -y \
    && apt-get install -y \
	  vim \
	  sudo \
	  git \
	  curl \
    zsh \
	  tmux \
    python 

EXPOSE 8080 8081 37241 1068
 
RUN useradd -ms /bin/bash tsmh
RUN usermod -aG sudo tsmh
RUN echo 'tsmh:tsmh' | chpasswd
RUN echo 'tsmh ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/tsmh 
USER tsmh
WORKDIR /home/tsmh

RUN git clone https://gitlab.com/tsmh/AutoLife.git


