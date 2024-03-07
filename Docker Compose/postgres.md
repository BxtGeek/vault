```
version: '3.9'

services:

  db:
    image: postgres
    restart: always
    shm_size: 128mb
    environment:
      TZ: Asia/Kolkata
      POSTGRES_PASSWORD: "Apple@01/24"
    volumes:
      - /data/docker/postgres:/var/lib/postgresql/data
    networks:
      - labnetwork

  adminer:
    image: adminer
    restart: always
    ports:
      - "8083:8080"
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true
