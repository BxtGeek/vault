```
version: '3'
services:
  filebrowser:
    image: filebrowser/filebrowser:latest
    ports:
      - '8081:80'
    volumes:
      - '/data:/srv'
      - '/data/docker/filebrowser/filebrowser.db:/database/filebrowser.db'
      - '/data/docker/filebrowser/settings.json:/config/settings.json'
    environment:
      - PUID=0
      - PGID=0
      - TZ=Asia/Kolkata
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
