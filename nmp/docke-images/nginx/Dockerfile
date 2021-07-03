FROM nginx:alpine

ENV TZ="Asia/Shanghai"

COPY conf/nginx.conf /etc/nginx/nginx.conf

# 在中国，需要更改源，将在.env中将 "CHANGE_SOURCE" 设置为true。
ARG CHANGE_SOURCE=true
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    # 用阿里云源替换 dl-cdn.alpinelinux.org
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories \
;fi

RUN apk update \
    && apk upgrade \
    && apk --update add logrotate \
    && apk add --no-cache openssl \
    && apk add --no-cache bash

RUN set -x ; \
    addgroup -g 82 -S nginx ; \
    adduser -u 82 -D -S -G nginx nginx && exit 0 ; exit 1

# 移除默认的default.conf配置文件
RUN  rm -rf /etc/nginx/conf.d/default.conf

#RUN set -ex \
#    && rm -rf /etc/nginx/conf.d/default.conf

EXPOSE 80 443