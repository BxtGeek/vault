```
---
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=1000
      - PGID=1000
      - TZ=Asia/Kolkata
    volumes:
      - /data/docker/jellyfin:/config
      - /data/download/series:/data/tvshows
      - /data/download/movies:/data/movies
    ports:
      - 8096:8096
    restart: unless-stopped
