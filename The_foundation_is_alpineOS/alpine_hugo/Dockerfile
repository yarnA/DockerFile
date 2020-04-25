FROM alpine:3.11.5
MAINTAINER Yang Lei  (yarn2856@163.com)

ENV HUGO_VERSION=0.68.0 \
    HUGO_SITE=/app/YangLxy \
    GIT_REPO=https://github.com/yarnA/hugo-theme-even.git 

RUN sed -i "s@http://dl-cdn.alpinelinux.org/@https://mirrors.huaweicloud.com/@g" /etc/apk/repositories \ 
    && apk --no-cache add \
        curl \
        git \
    && curl -SL https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_Linux-64bit.tar.gz \
        -o /tmp/hugo.tar.gz \
    && tar -xzf /tmp/hugo.tar.gz -C /tmp && mv /tmp/hugo /usr/local/bin/ \
    && mkdir -p ${HUGO_SITE}  && cd ${HUGO_SITE} && hugo new site .   \
    && git clone ${GIT_REPO}  themes/even &&  cp themes/even/exampleSite/config.toml  ./ \
    && apk del curl && rm -rf /tmp/*

WORKDIR ${HUGO_SITE}

VOLUME ${HUGO_SITE}/content/post/

EXPOSE 1313

CMD /usr/local/bin/hugo server \
    --bind 0.0.0.0 \
    --port 1313 \
    --navigateToChanged \
    --templateMetrics \
    --buildDrafts
