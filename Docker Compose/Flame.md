```
version: "3.8"
services:
  flame:
    image: pawelmalak/flame
    container_name: flame
    volumes:
      - /data/docker/flame:/app/data
      - /var/run/docker.sock:/var/run/docker.sock
    ports:
      - 80:5005
    environment:
      - PASSWORD=Apple@01/24
      - TZ=Asia/Kolkata
    restart: unless-stopped
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true


