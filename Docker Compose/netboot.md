```
version: '3'

services:
  netbootxyz:
    image: linuxserver/netbootxyz:latest
    container_name: netbootxyz
    environment:
      - PUID=0
      - PGID=0
      - TZ=Asia/Kolkata
      - PORT_RANGE=30000:30010 # Optional
    volumes:
      - /data/docker/netboot_xyz/config:/config
      - /data/template/iso:/assets
    ports:
      - "3000:3000"
      - "69:69/udp"
      - "8082:80" # Make sure the service inside the container listens on port 80
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
