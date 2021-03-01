FROM alpine:3.13

ENV PIKE_VERSION v8.0.1116

RUN set -eux; \
    apk add --no-cache --virtual .build-deps \
    make \
    build-base \
    gmp-dev \
    nettle-dev \
    && wget -O pike.tar.gz "https://pike.lysator.liu.se/pub/pike/latest-stable/Pike-${PIKE_VERSION}.tar.gz" \
    && mkdir -p /usr/src/pike \
    && tar -xzf pike.tar.gz -C /usr/src/pike --strip-components=1 \
    && rm pike.tar.gz \
    && cd /usr/src/pike \
    && make install \
    && cd / && rm -rf /usr/src/pike \
    && apk del --no-network .build-deps; \
    && pike --version

COPY docker-entrypoint.sh /usr/local/bin/
ENTRYPOINT ["docker-entrypoint.sh"]

CMD [ "pike" ]
