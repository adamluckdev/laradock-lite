ARG VERSION=latest
FROM mariadb:${VERSION}

#####################################
# Set Timezone
#####################################

ARG TZ=UTC
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone && chown -R mysql:root /var/lib/mysql/
COPY my.cnf /etc/mysql/conf.d/my.cnf

RUN chmod -R 644 /etc/mysql/conf.d/my.cnf

CMD ["mariadbd"]

EXPOSE 3306
