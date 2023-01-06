# Containers for MYSQL server, Scada-LTS and MQTT broker
 
  :warning: **WARNING:** Before starting, one must notice that the broker configuration file provided in `mosquitto-config/mosquitto.conf` allows external access **WITHOUT AUTHENTICATION** of any kind. For security reasons, it's recommended for **TESTING AND STUDYING ONLY**. If one needs any level of security, please set it editing the *mosquitto.conf* file with proper security settings, that may be found [here](https://mosquitto.org/man/mosquitto-conf-5.html).

## Setting up Docker
To run this application, one must install Docker Engine and Docker Compose. To do so, one can run:

```console
sudo curl -fsSL https://get.docker.com/ | sh
sudo apt-get install docker-compose unzip
```

> :bulb: **Tip**: Docker engine requires privileged access to run most commands. To give your user privileged access to Docker engine, run `usermod -aG docker <your-user>`, then logout and login again. 

 More information about Docker and Docker Compose can be found at [Docker Docs](https://docs.docker.com).

## Starting application
After installed, to pull images and start all three containers, run from the repository's main directory:

`docker-compose up -d`

Once all images are pulled, all services should be up and running.

Scada-LTS can be accessed in your browser via `<http://localhost:8080/Scada-LTS>`, and your mosquitto broker address sould be `<localhost:1883>`. <br> 

One might want as well start containers independently. It can be done by running:

`docker-compose up -d mysql` to start only mysql server; <br>
`docker-compose up -d scadalts` to start only Scada-LTS service, and <br>
`docker-compose up -d mosquitto` to start only MQTT broker.

One might as well want to keep logs and/or store MQTT data locally. To do so, uncomment `docker-compose.yml` commented lines.

Aditionally, more detailed information on Scada-LTS and reference code for this compose file can be found on [Scada-LTS Documentation](https://github.com/SCADA-LTS/Scada-LTS/wiki). 