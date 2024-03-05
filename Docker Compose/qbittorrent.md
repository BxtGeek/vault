```
---
services:
  qbittorrent:
    image: lscr.io/linuxserver/qbittorrent:latest
    container_name: qbittorrent
    environment:

      - PUID=0
      - PGID=0
      - TZ=Asia/Kolkata
      - WEBUI_PORT=8080
      - TORRENTING_PORT=6881

    volumes:
      - /data/docker/qbittorrent:/config
      - /data/download:/downloads
    ports:
      - 8080:8080
      - 6881:6881
      - 6881:6881/udp
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
