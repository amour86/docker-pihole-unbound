ARG PIHOLE_VERSION
FROM pihole/pihole:${PIHOLE_VERSION:-latest}
RUN apk update && apk add unbound
RUN apk add perl

COPY one-container/pihole-unbound/unbound.conf /opt/unbound.conf
COPY one-container/pihole-unbound/unbound-run /opt/unbound-run
COPY one-container/pihole-unbound/unbound.sh /opt/unbound.sh
COPY one-container/pihole-unbound/lighttpd-external.conf /etc/lighttpd/external.conf 
COPY one-container/pihole-unbound/unbound-pihole.conf /etc/unbound/unbound.conf.d/pi-hole.conf
COPY one-container/pihole-unbound/99-edns.conf /etc/dnsmasq.d/99-edns.conf
RUN mkdir -p /etc/services.d/unbound
RUN chmod +x /opt/unbound-run
COPY one-container/pihole-unbound/unbound-run /etc/services.d/unbound/run

ENTRYPOINT /opt/unbound-run
