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
      - 5005:5005
    environment:
      - PASSWORD=
      - TZ=Asia/Kolkata
    restart: unless-stopped
