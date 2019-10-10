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
Create a file named 'docker-compose.yml' and copy contents from https://github.com/klipperondocker/stack/blob/master/standard.yml

# (6) Create docker environment file
Create a file named ".env" and copy contents from https://github.com/klipperondocker/stack/blob/master/environment.env
Change "/folder/" to the folder you created for example "/home/yourname/klipperondocker/"

# (7) Start stack
```
docker-compose up -d
```
