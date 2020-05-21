FROM mysql:5.7

#set Mysql root password to changeit
ENV MYSQL_ROOT_PASSWORD=changeit

# Write one or more Docker command to copy the *.sql files to /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

#build the image
#run the image
#mysqladmin ping -uroot -p

# health check
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \ 
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD} || exit 1

# Where MySQL stores the database
# VOLUME /var/lib/mysql