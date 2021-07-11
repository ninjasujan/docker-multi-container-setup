#### Docker - working with multi container setup (Dockerfile)

3 basic containers in the applications

Frontend - React
Backend - Node and Express
Database - MongoDB

#### `Dockerizing Database`

1. First dockerize our DB service from docker image - mongodb
2. start the docker container (mongodb) in specific port

```
docker run --name mongodb --p 27017:27017 mongo
```

It will start the container and exposes the port 27017 in localhost

#### `Dockerizing Backend`

1. Write dockerfile to make necessary setup for running nodejs backend container
2. Start the container with docker run command
3. Please note in order to connect mongodb container from backend container please use **host.docker.internal**

`docker run -d --rm --name node-backend -p 80:80 backend`

#### `Dockersize the frontend application`

Follow the process to create backend conainer, since react uses nodejs in its dev environment

**Creating docker network to establish inter container communication**

1. create network

```
docker network create <network-name>
```

2. add --network flag with valid created network name in docker run command.

3. Replace and use container name wherever we use connection with another container.

4. optional - also bind port if we want in the container run command (based on your development reqirement) - usually container communicates in docker network through the container name
