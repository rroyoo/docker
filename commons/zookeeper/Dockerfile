FROM rroyoo/supervisord

MAINTAINER rroyo

ARG username=minion
ARG password=123456
# lastest at this moment
ARG zookeeper_version=3.4.10

# Create user 
RUN useradd -m $username -s /bin/bash
RUN echo "$username:$password" | chpasswd
RUN adduser $username sudo
RUN echo "$username ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

COPY conf/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# zookeeper install
ADD http://ftp.ps.pl/pub/apache/zookeeper/zookeeper-$zookeeper_version/zookeeper-$zookeeper_version.tar.gz /tmp

RUN tar xzf /tmp/zookeeper-$zookeeper_version.tar.gz -C /opt/
COPY conf/zoo.cfg /opt/zookeeper-$zookeeper_version/conf
RUN ln -s /opt/zookeeper-$zookeeper_version /opt/zookeeper

EXPOSE 2181
