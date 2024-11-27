```
version: '3.1'

services:
  ghost:
    image: ghost:5-alpine
    restart: unless-stopped
    ports:
      - 8005:2368
    environment:
      database__client: mysql
      database__connection__host: db
      database__connection__user: root
      database__connection__password: example
      database__connection__database: ghost
      url: http://localhost:8005
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/ghost/data:/var/lib/ghost/content
    networks:
      - labnetwork

  db:
    image: mysql:8.0
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: example
      
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/ghost/db:/var/lib/mysql
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
