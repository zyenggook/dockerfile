FROM ubuntu:16.04
MAINTAINER monaliza "1160804939@qq.com"

ENV LANG=C.UTF-8

#dns
COPY resolv.conf.d /etc/resolvconf/resolv.conf.d

#aliyun mirrors
COPY sources.list /etc/apt/
RUN rm -rf /etc/apt/sources.list.d
RUN apt-get update

#some tools
RUN apt-get install -y vim wget curl supervisor

#timezone
RUN echo "Asia/Shanghai" >/etc/timezone
RUN dpkg-reconfigure --frontend noninteractive tzdata

#supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

CMD ["/usr/bin/supervisord"]









