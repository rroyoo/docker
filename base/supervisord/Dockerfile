FROM ubuntu:16.04

MAINTAINER rroyo

# Install supervisor support
RUN apt update
RUN apt upgrade -y
RUN apt install -y supervisor apt-utils sudo less man wget software-properties-common openssh-server 
RUN mkdir -p /var/log/supervisor

RUN mkdir -p /var/run/sshd
RUN chmod 0755 /var/run/sshd

RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections
RUN add-apt-repository -y ppa:webupd8team/java
RUN apt update
RUN apt install -y oracle-java8-installer

EXPOSE 22
CMD ["supervisord"]