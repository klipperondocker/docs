# (1) Install docker on your platform


# (2) Create a folder to hold your data and enter it

```
mkdir klipperondocker
cd klipperondocker
chmod -R 777 .
```


# (3) Create initial folder structure

```
mkdir -p data/octoprint
mkdir -p data/klipper
mkdir -p data/klipper_log
mkdir -p data/uploads
```

# (4) Create a klipper config file
```
touch data/klipper/printer.cfg
```
you can copy an existing config or create a new one


# (5) Create a docker-compose.yml file with contents below
```
version: '3'

services:

  traefik:
    image: traefik:1.7
    command: 
      - "--api"
      - "--docker"
      - "--docker.exposedByDefault=false"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    ports:
      - 5080:80
    restart: always

  dockerapi:
    image: klipperondocker/dockerapi
    ports:
      - "8080:8080"
    volumes:
      - "/var/run/docker.sock:/var/run/docker.sock"
    restart: always

  octoprint:
    image: klipperondocker/octoprint:1.3.11
    restart: always
    privileged: true
    volumes:
     - "./data/octoprint:/root/.octoprint"
     - "./data/klipper:/klipper_config"
     - "./data/uploads:/uploads"
    environment:
      SOCAT_TYPE: "TCP"
      SOCAT_HOST: "klipper"
      SOCAT_PORT: "9999"
#      SOCAT_DEBUG: " -d -d -d -t 60 -T 60 "
    labels:
      - traefik.enable=true
      - traefik.frontend.rule=Host:0.0.0.0,127.0.0.1,localhost
      - traefik.port=5000
      - traefik.tags=sail3d
    restart: always

  klipper:
    image: klipperondocker/klipper:1b8a0079
    build: 
      context: ./src
      dockerfile: Dockerfile.klipper
    restart: always
    privileged: true
    volumes:
      - /dev:/hostdevices
      - ./data/klipper:/klipper_config
      - ./data/klipper_log:/klipper_log
      - ./data/uploads:/uploads
    environment:
      SER2NET_CONFIG: "9999:raw:0:/tmp/printer:115200 8DATABITS NONE 1STOPBIT -XONXOFF LOCAL -RTSCTS"
    restart: always
```
