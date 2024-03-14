```
version: '3.8'

services:
  keycloak:
    image: quay.io/keycloak/keycloak:24.0.1
    ports:
      - "8083:8080"
    environment:
      - KEYCLOAK_USER=admin
      - KEYCLOAK_PASSWORD=admin
      - TZ=Asia/Kolkata
    command: ["start-dev"]
    networks:
      - labnetwork
    volumes:
      - /data/docker/keycloak:/var/lib/postgresql/data

networks:
  labnetwork:
    external: true

```
