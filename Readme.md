# DAA 6.2 Projekt
That is a docker compose deployment

## Docker Compose Deployment

### Prerequisites
* You need Docker. For Windows and Mac I suggest using Docker Desktop: https://www.docker.com/products/docker-desktop

### Starting and Stopping
* For Linux and Mac you simply can use the following for starting the deployment
```
docker-compose up -d --build
```

And for tearing it down use:

```
docker-compose down
```

* Windows User
For starting the backend you need to know your ip address and than do:

```
.\start.sh -wp -hi 192.168.A.B  -wt 0
```

for tearing it down do:

```
.\start.sh -d
```

## Urls
localhost:8080
localhost:8080/alfresco
localhost:8080/share
localhost:8080/workspace