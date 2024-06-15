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
        tmux \
        vim \
        openvpn \
        iptables \
        easy-rsa \
        openvpn-auth-pam \
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

# Copy data
COPY rootfs /
