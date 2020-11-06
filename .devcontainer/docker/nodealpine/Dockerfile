FROM node:14-alpine

RUN apk add --no-cache sudo

ARG UID
ARG GID

RUN apk add --no-cache shadow \
    && groupmod --gid $GID node \
    && usermod --uid $UID --gid $GID node \
    && chown -R $UID:$GID /home/node \
    && apk del shadow
