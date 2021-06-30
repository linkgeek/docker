FROM mysql:latest

ENV TZ="Asia/Shanghai"

RUN ln -sf /usr/share/zoneinfo/${TZ} /etc/localtime && echo "{$TZ}" > /etc/timezone && chown -R mysql:root /var/lib/mysql/

COPY conf/my.cnf /etc/mysql/conf.d/my.cnf

#CMD ["mysqld", "--character-set-server=utf8mb4", "--collation-server=utf8mb4_unicode_ci"]


# 设置可以映射的端口
EXPOSE 3306