```
version: '3.1'

services:
  wordpress:
    image: wordpress
    restart: unless-stopped
    ports:
      - 8005:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: exampleuser
      WORDPRESS_DB_PASSWORD: examplepass
      WORDPRESS_DB_NAME: exampledb
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/wordpress/data:/var/www/html
    networks:
      - labnetwork

  db:
    image: mysql:8.0
    restart: unless-stopped
    environment:
      MYSQL_DATABASE: exampledb
      MYSQL_USER: exampleuser
      MYSQL_PASSWORD: examplepass
      MYSQL_RANDOM_ROOT_PASSWORD: '1'
    volumes:
      - /Users/manojkumar/Desktop/docker_images/docker_data/wordpress/db:/var/lib/mysql
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
```
