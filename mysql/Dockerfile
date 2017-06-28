FROM ubuntu:16.04
MAINTAINER "bruce0205@gmail.com"

RUN \
	apt-get update && \
	echo "mysql-server mysql-server/root_password password 53434976" | debconf-set-selections && \
    echo "mysql-server mysql-server/root_password_again password 53434976" | debconf-set-selections && \
    apt-get install -y mysql-server && \
    sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/mysql.conf.d/mysqld.cnf


COPY entrypoint.sh /entrypoint.sh
RUN chmod 755 /entrypoint.sh
COPY database.sql /database.sql
RUN chmod 755 /database.sql

EXPOSE 3306

#CMD ["/bin/bash","/sbin/entrypoint.sh"]
#ENTRYPOINT ["/bin/sh","/sbin/entrypoint.sh"]

#ENTRYPOINT ["/sbin/entrypoint.sh"]

#CMD ["/usr/bin/mysqld_safe"]

CMD ["/entrypoint.sh"]
