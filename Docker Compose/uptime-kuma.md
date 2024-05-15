```
version: "3.8"

services:
  uptime-kuma:
    image: louislam/uptime-kuma:1
    volumes:
      - /data/docker/uptime-kuma:/app/data
    ports:
      - "80:3001"
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
