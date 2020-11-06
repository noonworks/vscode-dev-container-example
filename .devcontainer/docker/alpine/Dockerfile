FROM alpine:3

RUN apk add --no-cache sudo

ARG USERNAME
ARG UID
ARG GID

RUN apk add --no-cache shadow \
    && groupadd --gid $GID $USERNAME \
    && useradd --uid $UID --gid $GID -m $USERNAME \
    && echo "$USERNAME ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME \
    && apk del shadow

USER $USERNAME
