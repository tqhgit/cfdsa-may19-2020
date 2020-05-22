FROM mysql:5.7

# set mysql the root password to "changeit"
ENV MYSQL_ROOT_PASSWORD=changeit

# write one or more docker commands to copy the sql files into /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# add health check v2
HEALTHCHECK --interval=20s --timeout=30s --start-period=5s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# where MySQL stores the database
VOLUME /var/lib/mysql