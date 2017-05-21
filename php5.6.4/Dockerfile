FROM ubuntu:15.04
MAINTAINER Jared Stenquist <jared@stenquist.com>

# Install base packages
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -yq install \
        vim \
        git \
        curl \
        supervisor \
        apache2 \
        libapache2-mod-php5 \
        php5-mysqlnd \
        php5-gd \
        php5-curl \
        php-pear \
        php5-mongo \
        php5-mcrypt \
        php5-memcached \
        memcached \
        php-apc && \
    rm -rf /var/lib/apt/lists/*

    RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    sed -i "s/variables_order.*/variables_order = \"EGPCS\"/g" /etc/php5/apache2/php.ini

RUN usermod -u 1000 www-data

# activate modules
RUN a2enmod rewrite headers deflate
RUN php5enmod mcrypt

# Update the PHP.ini file
RUN sed -i "s/short_open_tag = Off/short_open_tag = On/" /etc/php5/apache2/php.ini
RUN sed -i "s/display_errors = Off/display_errors = On/" /etc/php5/apache2/php.ini

# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
