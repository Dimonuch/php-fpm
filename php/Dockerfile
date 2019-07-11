FROM ubuntu:18.04
RUN apt-get update && \
    apt-get -y install wget apt-transport-https gnupg2 dirmngr && \
    wget -q https://packages.sury.org/php/apt.gpg -O- | apt-key add - && \
    echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php7.list && \
    apt-get update && \
    apt-get -y install php7.2 php7.2-fpm
RUN sed -i 's/^listen\ .*/listen\ =\ 0.0.0.0:9000/' /etc/php/7.2/fpm/pool.d/www.conf && \
    [[ -d /run/php ]] || mkdir /run/php
EXPOSE 9000
ENTRYPOINT ["/usr/sbin/php-fpm7.2"]
CMD ["-F", "--fpm-config", "/etc/php/7.2/fpm/php-fpm.conf"]
