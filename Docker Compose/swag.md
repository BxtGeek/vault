```
---
version: "2.1"
services:
  swag:
    image: lscr.io/linuxserver/swag
    container_name: swag
    cap_add:
      - NET_ADMIN
    environment:
      - PUID=0
      - PGID=0
      - TZ=Europe/London
      - URL=yourdomain.url
      - SUBDOMAINS=www,
      - VALIDATION=http
    - TZ=Asia/Kolkata
    volumes:
      - /data/docker/swag/config:/config
    ports:
      - 443:443
      - 80:80 #optional
    restart: unless-stopped
