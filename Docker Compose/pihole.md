```
version: "3"
services:
  pihole:
    container_name: pihole
    image: pihole/pihole:latest
    ports:
      - "53:53/tcp"
      - "53:53/udp"
      - "83:80/tcp"
    environment:
      TZ: Asia/Kolkata
      WEBPASSWORD: "Apple@01/24"
    volumes:
      - /data/docker/pihole/etc-pihole:/etc/pihole
      - /data/docker/pihole/etc-dnsmasq.d:/etc/dnsmasq.d
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
