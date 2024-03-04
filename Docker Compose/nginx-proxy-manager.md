```
version: '3.8'
services:
  app:
    image: 'jc21/nginx-proxy-manager:latest'
    restart: unless-stopped
    ports:
      - '80:80'
      - '81:81'
      - '443:443'
    volumes:
      - /data/docker/nginx-proxy-manager/data:/data
      - /data/docker/nginx-proxy-manager/letsencrypt:/etc/letsencrypt
