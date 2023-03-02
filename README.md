# Docker Compose Running MongoDB Replica Set

## Components
* `MongoDB:` is a NoSQL document-based database.
* `Prometheus:` open-source monitoring and alarming tool used to collect metrics from various systems.
* `Grafana:` multi-platform open-source analytics and interactive visualization tool. It provides charts, graphs, and alerts for the web when connected to supported data sources.
* `MongoDB Exporter:` will be used to convert MongoDB parameters into a format understandable by Prometheus.

## Contents
* [What is it?](#what-is-it)
* [Versions](#versions)
* [Are there any prerequisites?](#are-there-any-prerequisites)
* [How do I run the Replica Set?](#how-do-i-run-the-replica-set)
* [How do I access the Mongo Shells for each Instance?](#how-do-i-access-the-mongo-shells-for-each-instance)
* [How does it work?](#how-does-it-work)
* [Robo 3T](#robo-3t)
* [Thanks / Further Reading](#thanks--further-reading)

## Disclaimer
> :warning: **This setup is purely for local development purposes.**
> 
> This setup should not be used for production applications as it was not built with that in mind. 

## What is it?
This `docker-compose` setup starts a local mongo replica set with 3 instances running on: 
- mongodb1:27018
- mongodb2:27019
- mongodb3:27020

## Are there any prerequisites? 
* Docker
* Docker Compose
* The following in your `/etc/hosts` file:
```
127.0.0.1       mongodb1
127.0.0.1       mongodb2
127.0.0.1       mongodb3
```

## How do I run the Replica Set?
Simples:
```
docker-compose up -d
```

## How do I access the Mongo Shells for each Instance?
```
docker exec -it mongo1 sh -c "mongo --port 30001"
docker exec -it mongo2 sh -c "mongo --port 30002"
docker exec -it mongo3 sh -c "mongo --port 30003"
```

## Robo 3T
I used Robo 3T to test it locally and used the following config for the connection:
Download Robo3T: https://github.com/Studio3T/robomongo

![Robo 3T Config](https://github.com/UpSync-Dev/docker-compose-mongo-replica-set/raw/main/robo-3t.png)

## Connecting with URI
```
mongodb://mongodb1:27018,mongodb2:27019,mongodb3:27020/?replicaSet=replicaname
```

## Thanks / Further Reading
- [How to turn standalone MongoDB server into a replica set with Docker-Compose](https://zgadzaj.com/development/docker/docker-compose/turning-standalone-mongodb-server-into-a-replica-set-with-docker-compose)
- [Creating a MongoDB replica set using Docker 🍃](https://www.sohamkamani.com/blog/2016/06/30/docker-mongo-replica-set/)
- [asoorm/docker-compose-mongo-replicaset.yml](https://gist.github.com/asoorm/7822cc742831639c93affd734e97ce4f)
