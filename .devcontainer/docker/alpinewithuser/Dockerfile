FROM alpine:3

RUN apk add --no-cache sudo

#               ↓ DIFFERENT UID !
RUN adduser -u 1005 -D testuser \
    && echo "testuser ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/testuser\
    && chmod 0440 /etc/sudoers.d/testuser

ARG UID
ARG GID

# MODIFY UID
RUN apk add --no-cache shadow \
    && groupmod --gid $GID testuser \
    && usermod --uid $UID --gid $GID testuser \
    && chown -R $UID:$GID /home/testuser \
    && apk del shadow
