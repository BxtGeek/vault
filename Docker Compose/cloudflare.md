```
version: "3.8"

services:
  cloudflared:
    image: cloudflare/cloudflared:latest
    command: tunnel --no-autoupdate run --token <token-id>
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
