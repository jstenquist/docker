FROM mysql:5.7
ENV MYSQL_ROOT_PASSWORD=root \
  MYSQL_DATABASE=hqo_local
COPY db.sql /docker-entrypoint-initdb.d/db.sql
COPY _conf/custom.cnf /etc/mysql/conf.d/custom.cnf
EXPOSE 3306'