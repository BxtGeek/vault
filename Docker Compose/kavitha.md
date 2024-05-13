---
services:
  kavita:
    image: lscr.io/linuxserver/kavita:latest
    container_name: kavita
    environment:
      - PUID=0
      - PGID=0
      - TZ=Asia/Kolkata
    volumes:
      - /data/docker/kavita/config:/config
      - /data/docker/kavita/data:/data
      - /data/docker/kavita/manga/:/manga
      - /data/docker/kavita/comics/:/comics
      - /data/docker/kavita/epub/:/epub
    networks:
      - labnetwork
    ports:
      - 80:5000
    restart: unless-stopped

networks:
  labnetwork:
    external: true
