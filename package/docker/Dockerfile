FROM fluent/fluentd:v1.6-1

# Use root account to use apk
USER root

# below RUN includes plugin as examples elasticsearch is not required
# you may customize including plugins as you wish
RUN apk add --no-cache --update --virtual .build-deps \
    sudo build-base ruby-dev \
    && sudo gem install fluent-plugin-concat \
    && sudo gem install fluent-plugin-detect-exceptions \
    && sudo gem install fluent-plugin-multi-format-parser \
    && sudo gem install fluent-plugin-prometheus \
    && sudo gem install fluent-plugin-systemd \
    && sudo gem install fluent-plugin-logzio \
    && sudo gem install fluent-plugin-coralogix \
    && sudo gem install fluent-plugin-splunk-enterprise \
    && sudo gem install fluent-plugin-rewrite-tag-filter \
    && sudo gem sources --clear-all \
    && apk del .build-deps \
    && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

COPY fluent.conf /fluentd/etc/

USER fluent
