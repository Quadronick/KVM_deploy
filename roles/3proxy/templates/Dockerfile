#
# Just another SOCKS5 docker container.
# Using 3proxy server.
#

FROM alpine:{{ base_alpine_version }} as build
ENV  APP_VER={{ app_version }}
RUN  apk update --quiet --no-cache && \
     apk add build-base && \
     rm -rf /var/cache/apk/*

RUN  wget https://github.com/z3APA3A/3proxy/archive/${APP_VER}.tar.gz &&\
     tar xzfv ${APP_VER}.tar.gz -C /tmp &&\
     echo '#define ANONYMOUS 1' >> /tmp/3proxy-${APP_VER}/src/3proxy.h &&\
     make -C /tmp/3proxy-${APP_VER} -f Makefile.Linux &&\
     make -C /tmp/3proxy-${APP_VER} -f Makefile.Linux install &&\
     rm ${APP_VER}.tar.gz

FROM alpine:{{ base_alpine_version }}

COPY --from=build /usr/local/bin/3proxy /usr/local/bin/3proxy

CMD  ["/usr/local/bin/3proxy", "/etc/3proxy/3proxy.cfg"]
