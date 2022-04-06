
FROM python:alpine
LABEL maintainer="Evine Deng <evinedeng@foxmail.com>"
ENV PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
    HOME=/root \
    LANG=zh_CN.UTF-8 \
    SHELL=/bin/bash \
    PS1="\u@\h:\w \$ "
RUN apk update -f \
    && apk --no-cache add -f \
       bash \
       s6-overlay \
       openssl \
       coreutils \
       moreutils \
       git \
       wget \
       curl \
       nano \
       tzdata \
       gcc \
       g++ \
       clang \
    && ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo "Asia/Shanghai" > /etc/timezone \
    && python -m pip install --upgrade pip \
    && rm -rf \
       /tmp/* \
       /root/.cache
COPY --from=nevinee/loop:latest / /
COPY s6-overlay /
WORKDIR /root
ENTRYPOINT ["/init"]
