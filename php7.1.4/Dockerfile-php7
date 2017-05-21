FROM ubuntu:16.04
MAINTAINER Jared Stenquist <jared@stenquist.com>

RUN apt-get update \
	&& apt-get install -y software-properties-common \
  && apt-get install -y supervisor \
	&& apt-get install -y language-pack-en-base \
	&& LC_ALL=en_US.UTF-8 add-apt-repository -y ppa:ondrej/php \
	&& apt-get update \
  && apt-get -y install memcached unzip apache2 libapache2-mod-php7.1 php7.1 php-xml php7.1-xml php7.1-bcmath php7.1-mbstring php-uuid php-libsodium php7.1-cli php7.1-mbstring sqlite3 php7.1-mysql php-apcu php-apcu-bc php-imagick php-memcached php-pear curl imagemagick php7.1-dev php7.1-phpdbg php7.1-gd npm nodejs-legacy php7.1-json php7.1-curl php7.1-sqlite3 php7.1-intl apache2 vim php-redis git-core wget libsasl2-dev libssl-dev libsslcommon2-dev libcurl4-openssl-dev autoconf g++ make openssl libssl-dev libcurl4-openssl-dev pkg-config libsasl2-dev libpcre3-dev \
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
