FROM rroyoo/supervisord

MAINTAINER rroyo

ARG username=minion
ARG password=123456
# latest at this moment
ARG kafka_version=0.11.0.2
ARG kafka=kafka_2.12-$kafka_version

# Create user 
RUN useradd -m $username -s /bin/bash
RUN echo "$username:$password" | chpasswd
RUN adduser $username sudo
RUN echo "$username ALL=(ALL) NOPASSWD: ALL" >> /etc/sudoers

COPY conf/supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# zookeeper install
ADD http://ftp.ps.pl/pub/apache/kafka/$kafka_version/$kafka.tgz /tmp

RUN tar xzf /tmp/$kafka.tgz -C /opt/
RUN ln -s /opt/$kafka /opt/kafka

COPY conf/server.properties /opt/kafka/config/server.properties

EXPOSE 9092
