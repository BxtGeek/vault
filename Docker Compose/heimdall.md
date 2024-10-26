```
version: "3"
services:
  heimdall:
    image: lscr.io/linuxserver/heimdall:latest
    container_name: heimdall
    environment:
      - PUID=501
      - PGID=20
      - TZ=Asia/Kolkata
    volumes:
      - /path/to/heimdall/config:/config
    ports:
      - 84:80
      - 444:443
    restart: unless-stopped
```
