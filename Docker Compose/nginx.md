```
version: "3.8"

services:
  nginx:
    image: lscr.io/linuxserver/nginx:latest
    container_name: nginx
    environment:
      - PUID=501
      - PGID=20
      - TZ=Asia/Kolkata
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/nginx:/config
    ports:
      - 8001:80
      - 442:443
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
