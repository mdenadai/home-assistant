ARG BUILD_FROM
FROM $BUILD_FROM

# Setup base
RUN \
    set -x \ 
    && apk add --no-cache \
        bash-completion \
        pulseaudio-utils \
        alsa-plugins-pulse \
        bluez \
        git \
        libuv \
        mosquitto-clients \
        nano \
        openssh \
        pwgen \
        tmux \
        vim \
        nginx \
        fcgiwrap \
        sudo \
        ffplay \
        at \
    \
    && apk add --no-cache --virtual .build-dependencies \
        bsd-compat-headers \
        build-base \
        linux-headers \
        cmake \
        json-c-dev \
        libuv-dev \
        openssl-dev \
        zlib-dev \
    \
    && apk del --no-cache --purge .build-dependencies \
    && rm -f -r \
        /root/.cache \
        /root/.cmake \
        /tmp/*

RUN echo nginx >> /etc/at.allow

# Copy data
COPY rootfs /
