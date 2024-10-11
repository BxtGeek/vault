```
version: '3.8'

services:
  portainer:
    image: portainer/portainer-ce
    command: > 
      -H tcp://agent:9001 --tlsskipverify
    ports:
      - "80:9000"
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - portainer_data:/data
    networks:
      - labnetwork

networks:
  labnetwork:
    external: true

volumes:
  portainer_data:
    name: portainer_data
```
