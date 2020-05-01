FROM alpine:latest

MAINTAINER Yang Lei  (yarn2856@163.com)
#Modified from https://hub.docker.com/r/saoneth/apline-glibc/dockerfile

# Here we install GNU libc (aka glibc) and set C.UTF-8 locale as default.

RUN { \
  sed -i "s@http://dl-cdn.alpinelinux.org/@https://mirrors.huaweicloud.com/@g" /etc/apk/repositories && \
  apk add --no-cache --virtual=.build-dependencies curl ca-certificates wget jq && \
  curl 'https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub' -o /etc/apk/keys/sgerrand.rsa.pub&& \
  curl 'https://api.github.com/repos/sgerrand/alpine-pkg-glibc/releases' \
  | jq '.[0].assets | map(select( .name | contains(".apk") )) | map(select( .name | contains("-dev") | not )) | .[].browser_download_url' \
  |xargs wget  --content-disposition &&  \
  apk add --no-cache glibc-*.apk &&  \
  \
  rm "/etc/apk/keys/sgerrand.rsa.pub" &&  \
  /usr/glibc-compat/bin/localedef --force --inputfile POSIX --charmap UTF-8 "$LANG" || true &&  \
  echo "export LANG=$LANG" > /etc/profile.d/locale.sh && \
  \
  apk del glibc-i18n .build-dependencies curl wget jq && \
  \
  rm "/root/.wget-hsts"; \
  rm glibc-*.apk; \
}

ENV LANG=C.UTF-8
