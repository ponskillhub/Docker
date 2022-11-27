# Run a docker container in detached mode

```
docker run -p 3000:80 -d --name feedback-app feedback-node
```

# Volumes

### Volumes are folders in host machine, which are mounted into container

### Volumes persist data even after the container is shut down

# Two types of external data storages

1. Volumes - managed by Docker
   - Anonymous Volumes
   - Named Volumes
2. Bind Mounds - managed by you

## Build ananomyms volumes

```
FROM node:14
WORKDIR /app
COPY package.json /app
RUN npm install
COPY . .
EXPOSE 80
VOLUME [ "/app/feedback" ]
CMD ["node", "server.js"]
```

## List the docker volumes

```
docker volume ls
```

## run a container with named local volume

```
docker run -p 3000:80 -d --rm --name feedback-app -v feedback:/app/feedback ponjagannath/feedback-app
```

# Delete anonymous volumes

```
docker volume rm VOL_NAME
```

```
docker volume prune
```

# Bind mounts - managed by you

```
docker run -p 3000:80 -d --rm --name feedback-app -v "C:/Users/Ponjagannath.T/Documents/github-ponjagannath/Docker/3 Managing Data/data-volumes-01-starting-setup:/app" feedback:/app/feedback -v ponjagannath/feedback-app
```

```
docker run -p 3000:80 -d --rm --name feedback-app -v "/mnt/c/Users/Ponjagannath.T/Documents/github-ponjagannath/Docker/3 Managing Data/data-volumes-01-starting-setup":/app -v feedback:/app/feedback -v /app/node_modules ponjagannath/feedback-app
```

# Read volumes

```
docker run -p 3000:80 -d --rm --name feedback-app -v "/mnt/c/Users/Ponjagannath.T/Documents/github-ponjagannath/Docker/3 Managing Data/data-volumes-01-starting-setup":/app:RO: -v feedback:/app/feedback -v /app/node_modules ponjagannath/feedback-app
```

# Create a Docker volume

```
docker volume create <name of the volume>
```

# Inspect a volume

```
docker inspect <name of the volume>
```

# Remove a volume

```
docker volume rm feedback
```

# .dockerignore

### define the files to ignore duing image build copy.

# environment variables

- can be used every wheren including the CMD and the application code

.env

```
PORT=8000
```

use the environment file while running the container

```
docker run .... env-file ./.env
```

# Arguments

- cant be used in CMD and in application code

in the Dockerfile

```
ARG DEFAULT_PORT=80
```

in the docker build command

```
Docker build -t feedback-node:dev --build-arg DEFAULT_PORT=8000
```
