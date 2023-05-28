## Run a container

### Run the node image from dockerhub

```sh
docker run node
```

## Display all the containers

```sh
docker ps -a
```

## docker interactive session

```
docker run -it node
```

### to exit out of node enter .exit

```
.exit
```

## Docker file to build a image from node base image
## Write the below to a file named Docker File

```
FROM node

WORKDIR /app

COPY . /app

RUN npm install

EXPOSE 80

CMD ["node", "server.js"]
```

## view the running docker containers

```
docker ps
```

## stop a container

```
docker stop boring_murdock
```

## connect a port number on the host with the exposed port of the container

```
docker run -p 3000:80 cf560b5ea06169ad324e3ecad880b816422eee0ae678ca8bbf4f70f92e06414b
```

## List all the docker commands

```
docker --help
```

## Restart a stopped container

```
docker start <container name>
```

## Docker run - default: attached mode

## Docker start - default: detached mode

## Run container in detached mode

```
docker run -p 3000:80 -d cf560b5ea06169ad324e3ecad880b816422eee0ae678ca8bbf4f70f92e06414b
```

## Attach a container

```
docker attach f243999392b95731ebc4026801ee9674e1a15d7e694b39ea9dfa46bfcedfd683
```

## Docker logs

```
docker logs goofy_lovelace
```

```
docker logs -f goofy_lovelace
```

## Restart a container in attached mode

```
docker start -a goofy_lovelace
```

## Start a container in attached, interactive mode

```
docker start -i -a sharp_nobel
```

## Remove a docker container

```
docker rm 04f5a9b02326
```

## List all the images

```
docker images
```

## Remove an image

```
docker rmi 7a8965d6553e
```

## Remove all stopped container

```
docker container prune
```

## Remove all unused images

```
docker image prune
```

## Remove a container once its stopped

```
docker run --rm 49176f190c7e
```

## image inspect

```
docker image inspect <image id>
```

## Copy a file to a container

```
docker cp test.txt practical_yalow:/test.txt
```

## Copy a file from container to local folder

```
docker cp practical_yalow:/test.txt .
```

## Naming and tagging images and containers

```
docker run -p 3000:80 --name usergivenname cf560b5ea06169ad324e3ecad880b816422eee0ae678ca8bbf4f70f92e06414b
```

### image name has two parts - name : tag

```
docker build -t goals:latest .
```

## Retagging a docker image

```
docker tag <old tag> <new tag>
```

## push a image to DockerHub

```
docker login -u "ponjagannath" -p "iampon@07091984d" docker.io
docker push ponjagannath/pon-airflow
```
