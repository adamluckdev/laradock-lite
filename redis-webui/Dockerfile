FROM erikdubbelboer/phpredisadmin

ENV ADMIN_USER larapod
ENV ADMIN_PASS larapod
ENV REDIS_1_HOST 127.0.0.1
ENV REDIS_1_PORT 6379

EXPOSE 8081
ENTRYPOINT [ "tini", "--", "php", "-S", "0.0.0.0:8081" ]
