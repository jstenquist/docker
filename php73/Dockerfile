FROM ubuntu:18.04
LABEL maintainer="jared@stenquist.com"

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
	&& apt-get install -y software-properties-common \
    && apt-get install -y supervisor \
	&& apt-get install -y language-pack-en-base \
	&& LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
	&& apt-get update \
    && apt-get -y install unzip apache2 libapache2-mod-php7.3 php7.3 php-xml php7.3-xml php7.3-bcmath php7.3-mbstring php-uuid php7.3-cli php7.3-mbstring php7.3-mysql php-apcu php-apcu-bc php-memcached php-pear curl php7.3-dev php7.3-json php7.3-curl php7.3-intl vim php-redis git-core wget libsasl2-dev libssl-dev libcurl4-openssl-dev autoconf g++ make openssl libssl-dev libcurl4-openssl-dev pkg-config libsasl2-dev libpcre3-dev \
	&& a2enmod rewrite headers deflate proxy proxy_http ssl \
	&& pecl channel-update pecl.php.net \
	&& mkdir -p /var/run/apache2  /var/log/apache2 /var/lock/apache2 \
	&& chown -R www-data:www-data /var/run/apache2 /var/log/apache2 /var/lock/apache2 \
	&& usermod -u 1000 www-data \
	&& echo "ServerName localhost" >> /etc/apache2/apache2.conf

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2