```
version: "3.8"

services:
  nextcloud:
    image: lscr.io/linuxserver/nextcloud:latest
    container_name: nextcloud
    environment:
      - PUID=501
      - PGID=20
      - TZ=Etc/UTC
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/nextcloud/config:/config
      - /Users/manojkumar/Desktop/docker_images/docker_data/nextcloud/data:/data
    ports:
      - 8004:443
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
