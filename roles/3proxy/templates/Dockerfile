#
# Just another SOCKS5 docker container.
# Using 3proxy server.
#

FROM alpine:latest
ENV  APP_VER=0.8.11
RUN  apk update --quiet && apk add build-base

RUN  wget https://github.com/z3APA3A/3proxy/archive/${APP_VER}.tar.gz &&\
     tar xzfv ${APP_VER}.tar.gz -C /tmp &&\
     echo '#define ANONYMOUS 1' >> /tmp/3proxy-${APP_VER}/src/3proxy.h &&\
     make -C /tmp/3proxy-${APP_VER} -f Makefile.Linux &&\
     make -C /tmp/3proxy-${APP_VER} -f Makefile.Linux install &&\
     rm ${APP_VER}.tar.gz &&\
     mkdir /etc/3proxy && \
     ln -sf /dev/stdout /var/log/3proxy.log

CMD  ["/usr/local/bin/3proxy", "/etc/3proxy/3proxy.cfg"]
