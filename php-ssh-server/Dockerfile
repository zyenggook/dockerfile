FROM monaliza/ubuntu
MAINTAINER monaliza "1160804939@qq.com"

# motd welcome
ADD 01-welcome /etc/update-motd.d/
RUN run-parts /etc/update-motd.d/

# apt update
RUN apt-get update

# tengine
RUN apt-get install -y build-essential libpcre3-dev libssl-dev cronolog 
RUN \
	mkdir /server && \
	curl http://tengine.taobao.org/download/tengine-2.1.0.tar.gz >/tmp/tengine-2.1.0.tar.gz && \
	cd /tmp/ && \
	tar -xvf tengine-2.1.0.tar.gz && \
	cd tengine-2.1.0 && \
	./configure --prefix=/server/tengine && \
	make && make install && \
	rm -rf /tmp/tengine* && \
	chown www-data /server/tengine/logs -R

ADD nginx.conf /server/tengine/conf/
ADD sites/ /server/tengine/conf/sites

# php5-fpm
RUN apt-get install -y php5-mysql php5-fpm php5-cli php5-curl php5-json php5-mcrypt php5-gd
ADD php-fpm.conf /etc/php5/fpm/php-fpm.conf
RUN ln -s /etc/php5/mods-available/mcrypt.ini /etc/php5/fpm/conf.d/mcrypt.ini


#sshd
RUN apt-get install -y openssh-server
RUN mkdir /var/run/sshd
ADD sshd_config /etc/ssh/sshd_config
ADD authorized_keys /root/.ssh/authorized_keys

# supervisord
ADD supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# Expose ports.
EXPOSE 80
EXPOSE 443
EXPOSE 22
