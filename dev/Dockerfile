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
    python \
    openssh-server

EXPOSE 8080 8081 22
 
RUN useradd -ms /usr/bin/zsh tsmh
RUN usermod -aG sudo tsmh
RUN echo 'tsmh:tsmh' | chpasswd
RUN echo 'tsmh ALL=(ALL) NOPASSWD:ALL' > /etc/sudoers.d/tsmh 
RUN mkdir /var/run/sshd

CMD ["/usr/sbin/sshd", "-D"]

