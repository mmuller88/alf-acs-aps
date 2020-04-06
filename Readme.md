# DAA 6.2 Projekt
That is a docker compose deployment

## Docker Compose Deployment

### Prerequisites
* You need Docker. For Windows and Mac I suggest using Docker Desktop: https://www.docker.com/products/docker-desktop . After installing the Docker Desktop Client remember to assign more memory to it. Per default the Docker Desktop Client just gets 2 GB RAM which is way to less for ACS. At minimum you have to assign 12 GB to it!
* For the Quay images you need a login for www.quay.io . Ask Nenad or an other colleage for the credentials and than do:

```
docker login quay.io
```

### Starting and Stopping
General informations:
* It generates volume data in the project directory /data for alf-repo_data, mysql_data and solr-data
* it generates logs in the project folder /logs for alfresco, mysql and share
* If you want to create ACS fresh again delete those folders!!


* For Linux and Mac you simply can use the following for starting the deployment
```
docker-compose up -d --build
```

or stopping it do:

```
docker-compose stop
```

And for tearing it down use:

```
docker-compose down
```

* Windows User
For starting the backend you need to know your ip address and than do:

```
.\start.sh -wp -wt 0
```

for stopping it do:

```
docker-compose stop
```

for tearing it down do:

```
.\start.sh -d
```

## Urls
* localhost:8080
* localhost:8080/alfresco
* localhost:8080/share
* localhost:8080/workspace
* localhost:8080/api-explorer