FROM    ubuntu:precise
MAINTAINER jp@barreverte.fr

RUN apt-get update -y

# install sshd
RUN apt-get install -y openssh-server python python-keyczar
RUN mkdir /var/run/sshd

# create install user
RUN echo "root:toto" | chpasswd

EXPOSE 22
ENTRYPOINT ["/usr/sbin/sshd"]
