FROM centos:7
MAINTAINER "tmasu"

# add yum repository
RUN yum -y install epel-release
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

# install apache2.4
RUN yum -y install --enablerepo=remi httpd

# install php7.1
RUN yum remove php-*
RUN yum -y install --enablerepo=remi,remi-php71 php php-bz2 php-devel php-xml php-mbstring php-pdo php-gd php-mysql wget

# composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# install zip, unzip
RUN yum -y install zip unzip

# install git
RUN yum -y install git

# install ssh
RUN yum -y install openssh-server

# install net-tools
RUN yum -y install net-tools

# install MariaDB
RUN yum -y install mariadb-server

# enable service.
RUN systemctl enable httpd
RUN systemctl enable sshd.service
RUN systemctl enable mariadb

# install wordpress
# RUN wget https://ja.wordpress.org/latest-ja.tar.gz -O /tmp/wp-latest.tar.gz
# RUN tar -zxvf /tmp/wp-latest.tar.gz -C /var/www/html/
# RUN chown -R apache:apache /var/www/html/wordpress

# change password
RUN echo 'root:root' | chpasswd

# exec.
CMD ["/sbin/init"]
