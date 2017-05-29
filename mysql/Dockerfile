FROM ubuntu:16.04
LABEL maintainer "bruce0205@gmail.com"

USER root

RUN \
	apt-get update && \
	echo "mysql-server mysql-server/root_password password 53434976" | debconf-set-selections && \
    echo "mysql-server mysql-server/root_password_again password 53434976" | debconf-set-selections && \
    apt-get install -y mysql-server && \
    sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/mysql.conf.d/mysqld.cnf


COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod +x /sbin/entrypoint.sh
COPY database.sql /sbin/database.sql
RUN chmod +x /sbin/database.sql

EXPOSE 3306

CMD ["/bin/bash","/sbin/entrypoint.sh"]
