# Build image

```
docker build -t favorites-node .
```

# Run mongo

```
docker run -d --name mongodb mongo
```

# Inspect a docker container

```
docker inspect 8c9254eba529bdf6256cf2ee6c1a9f259e1a4aad2388aa7139b49bee5cb687d
```

```
"NetworkSettings": {
            "Bridge": "",
            "SandboxID": "4157ffeea1708784951582a8480ae9f8c38432c8f0bd1f26a9962f1812b5739d",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "27017/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/4157ffeea170",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "ace56dcfd35526720fa3b3ec1723af27c1254f1c9cc439bf7a1ef52f566e3ef5",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "84b75f4194f0d324b27c1b595b9daf39b30fb1b1fbd1a2ceb71783e139632427",
                    "EndpointID": "ace56dcfd35526720fa3b3ec1723af27c1254f1c9cc439bf7a1ef52f566e3ef5",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }

```

## Build the application docker image after the mongodb ip address was updated in the application

```
docker build -t favorites-node .
```

## Run the favorites-node image's container

```
docker run --name favorites -d --rm -p 3000:3000 favorites-node
```

## remove all stoped container

```
docker container prune
```

# Create network

```
docker network create favorite-network
```

## Show the existing networks

```
docker network ls
```

## run the mongodb container in favorite-network

```
docker run -d --name mongodb --network favorite-network mongo
```

## change the ipaddress to mongodb ( which is the container name of the mongo image)

```js
mongoose.connect(
  "mongodb://mongodb:27017/swfavorites",
  { useNewUrlParser: true },
  (err) => {
    if (err) {
      console.log(err);
    } else {
      app.listen(3000);
    }
  }
);
```

## Rebuild the app image

```
docker build -t favorites-node .
```

```
docker run --name favorites --network favorite-network -d --rm -p 3000:3000 favorites-node
```
