# Containers for MYSQL server, Scada-LTS and MQTT broker
 
  :warning: **WARNING:** Before starting, one must notice that the broker configuration file provided in [mosquitto-config/mosquitto.conf](/mosquitto-config/mosquitto.conf) allows external access **WITHOUT AUTHENTICATION** of any kind. For security reasons, it's recommended for **TESTING AND STUDYING ONLY**. If one needs any level of security, please set it editing the *mosquitto.conf* file with proper security settings, that may be found [here](https://mosquitto.org/man/mosquitto-conf-5.html).

## Setting up Docker
To run this application, one must install Docker Engine and Docker Compose. To do so, one can run:

```console
sudo curl -fsSL https://get.docker.com/ | sh
sudo apt-get install docker-compose unzip
```

> :bulb: ***TIP:*** Docker engine requires privileged access to run most commands. To give your user privileged access to Docker engine, run `usermod -aG docker <your-user>`, then logout and login again. 

More information about Docker and Docker Compose can be found in the [Reference Docs section](/AndreFavotto/mqtt-scadalts#reference-docs), in the end of this document.

## Starting application
After installed, to pull images and start all three containers, run from the repository's main directory:

`docker-compose up -d`

Once all images are pulled, all services should be up and running.

Scada-LTS can be accessed in your browser via `<http://localhost:8080/Scada-LTS>` with default user admin/admin. The mosquitto broker address sould be `<localhost:1883>`.  

All services can be stopped by running `docker-compose stop` in the shell terminal.

## Start services independently

One might want as well to start or stop services independently. For MQTT broker, run:

`docker-compose up -d mosquitto` or `docker-compose stop mosquitto` 

> OBS: If keeping logs and/or store MQTT data locally is needed, uncomment [docker-compose.yml](/docker-compose.yml) commented lines.

Similarly, the same can be done to Scada-LTS running `docker-compose up -d scadalts` or `docker-compose stop scadalts`. As it depends on mysql database, if not running, the mysql container will start automatically as well.

## Reference Docs

- [Docker Docs](https://docs.docker.com)
- [Scada-LTS Documentation](https://github.com/SCADA-LTS/Scada-LTS/wiki). 
- [Mosquitto configuration file](https://mosquitto.org/man/mosquitto-conf-5.html)