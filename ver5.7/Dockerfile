FROM mysql:5.7-debian

RUN apt-get update \
    && apt-get install -y wget unzip \
    && wget http://downloads.mysql.com/docs/sakila-db.zip \
    && unzip sakila-db.zip \
    && mv sakila-db/sakila-schema.sql /docker-entrypoint-initdb.d/01_sakila-schema.sql \
    && mv sakila-db/sakila-data.sql /docker-entrypoint-initdb.d/02_sakila-data.sql