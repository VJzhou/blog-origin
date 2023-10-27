ARG NODE_VERSION=14

FROM node:${NODE_VERSION}-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

RUN apk update \
    &&  apk upgrade \
    && apk add --no-cache \
    bash \
    tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && apk del tzdata \
    && apk add \
    git \
    nodejs \
    && npm config set registry http://registry.npm.taobao.org/ \
    && npm install hexo-cli -g

COPY docker-entrypoint.sh /usr/local/bin/

RUN chmod a+x /usr/local/bin/docker-entrypoint.sh

ENTRYPOINT [ "docker-entrypoint.sh" ]
