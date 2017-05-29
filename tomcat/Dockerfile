FROM ubuntu:16.04
LABEL maintainer "bruce0205@gmail.com"

USER root

RUN \
	apt-get update && \
    apt-get install -y vim && \
    apt-get install -y git 
#&& \
    #apt-get install -y software-properties-common && \
    #add-apt-repository -y ppa:webupd8team/java && \
    #apt-get update && \
    #echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections && \
    #echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 seen true" | debconf-set-selections && \
    #apt-get install -y oracle-java8-installer && \
    #export JAVA_HOME="/usr/lib/jvm/java-8-oracle/" && \
    #echo 'JAVA_HOME="/usr/lib/jvm/java-8-oracle/"' >> /etc/environment

RUN \
    echo "mysql-server mysql-server/root_password password 53434976" | debconf-set-selections && \
    echo "mysql-server mysql-server/root_password_again password 53434976" | debconf-set-selections && \
    apt-get install -y mysql-server && \
    sed -i "s/.*bind-address.*/bind-address = 0.0.0.0/" /etc/mysql/mysql.conf.d/mysqld.cnf


WORKDIR /tmp
COPY ./test.txt ./


WORKDIR /etc/mysql

EXPOSE 3306
#ENTRYPOINT ["/bin/echo", "Hello"]
CMD ["mysqld"]
