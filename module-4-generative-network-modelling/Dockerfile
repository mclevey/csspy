FROM tiagopeixoto/graph-tool

USER root
RUN apk update && apk add --no-cache \
    xauth \
    xclock \
    && rm -rf /var/cache/apk/*

USER user
WORKDIR /home/user
