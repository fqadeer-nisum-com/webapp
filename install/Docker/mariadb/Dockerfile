FROM mariadb

RUN apt-get update
RUN apt-get install -y vim
RUN apt-get install net-tools

ADD mariadb/schema.sql /docker-entrypoint-initdb.d/schema.sql
