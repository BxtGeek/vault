```
---
services:
  jellyfin:
    image: lscr.io/linuxserver/jellyfin:latest
    container_name: jellyfin
    environment:
      - PUID=0
      - PGID=0
      - TZ=Asia/Kolkata
    volumes:
      - /data/docker/jellyfin:/config
      - /data/download/series:/data/tvshows
      - /data/download/movies:/data/movies
    ports:
      - 8096:8096
    restart: unless-stopped
