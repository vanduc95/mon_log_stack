FROM fluent/fluentd:v1.15
# Use root account to use apk
USER root

RUN apk add --no-cache --update --virtual .build-deps \
    sudo build-base ruby-dev \
    && gem install fluent-plugin-elasticsearch \
    && gem install fluent-plugin-rewrite-tag-filter \
    && gem install fluent-plugin-prometheus \
    && gem install elasticsearch-xpack \
    && gem sources --clear-all \
    && apk del .build-deps \
    && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

USER fluent
