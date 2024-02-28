
https://dockge.kuma.pet/

```yml
version: "3.8"
services:
  dockge:
    image: louislam/dockge:1
    restart: unless-stopped
    ports:
      - 5001:5001
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
      - ./data:/app/data
      # Stacks Directory
      # ⚠️ READ IT CAREFULLY. If you did it wrong, your data could end up writing into a WRONG PATH.
      # ⚠️ 1. FULL path only. No relative path (MUST)
      # ⚠️ 2. Left Stacks Path === Right Stacks Path (MUST)
      - /mnt/NFSNAS/Linux/Docker:/mnt/NFSNAS/Linux/Docker
    environment:
      # Tell Dockge where to find the stacks
      # This only applies to a NFS Mounted on this particular system make sure this line is correct
      - DOCKGE_STACKS_DIR=/mnt/NFSNAS/Linux/Docker```
