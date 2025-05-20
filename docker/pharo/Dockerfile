FROM ghcr.io/ba-st/pharo:v12.0.1

COPY --chown=pharo:users ./httpbin* ./
USER root
RUN set -eu; \
  apt update; \
  apt upgrade --assume-yes; \
  apt install --assume-yes --no-install-recommends netcat-openbsd; \
  apt clean; \
  rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*; \
  ln -s /opt/pharo/httpbin /usr/local/bin/httpbin; \
  ln -s /opt/pharo/httpbin-list /usr/local/bin/httpbin-list; \
  ln -s /opt/pharo/httpbin-explain /usr/local/bin/httpbin-explain; \
  ln -s /opt/pharo/httpbin-start /usr/local/bin/httpbin-start; \
  ln -s /opt/pharo/httpbin-healthcheck /usr/local/bin/httpbin-healthcheck; \
  chmod a+x /usr/local/bin/httpbin*; \
  true

USER pharo

HEALTHCHECK CMD [ "httpbin-healthcheck"]
