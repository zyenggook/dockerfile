FROM monaliza/ubuntu
MAINTAINER monaliza "1160804939@qq.com"

# tengine
RUN apt-get update && apt-get install -y build-essential unzip 
RUN \
	cd /tmp && \
	wget --no-check-certificate https://github.com/ideawu/ssdb/archive/master.zip && \
	unzip master.zip && \
	cd ssdb-master && \
	make && make install && \
	rm -rf /tmp/* 

ADD ssdb.conf /usr/local/ssdb/

ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Expose ports.
EXPOSE 8888
