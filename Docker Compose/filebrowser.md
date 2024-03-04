version: '2'
services:
  filegator:
    container_name: filegator
    image: filegator/filegator
    ports:
      - 8081:8080
    volumes:
      - /data/:/var/www/filegator/repository
      - /data/docker/filegator:/var/www/filegator/private/users.json
    environment:
      - TZ=Asia/Kolkata
    restart: unless-stopped
