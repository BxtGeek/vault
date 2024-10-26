```
version: "3"
services:
  vaultwarden:
    image: vaultwarden/server:latest
    container_name: vaultwarden
    restart: unless-stopped
    ports:
      - 82:80
    volumes:
      - /Users/manojkumar/Desktop/Docker/vaultwarden:/data
    environment:
      - TZ=Asia/Kolkata
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
