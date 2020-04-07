# 6.2 Projekt
That is a docker compose deployment.

## Prerequisites
* You need Docker. For Windows and Mac I suggest using Docker Desktop: https://www.docker.com/products/docker-desktop . After installing the Docker Desktop Client remember to assign more memory to it. Per default the Docker Desktop Client just gets 2 GB RAM which is way to less for ACS. At minimum you have to assign 12 GB to it!
* For the Quay images you need a login for www.quay.io .

```
docker login quay.io
```

## Deployments
As deploying ACS + APS consumes a lot memory I decided to divide the Docker Compose deployment in three Deployments:

1) Only ACS (docker-compose-base.yml + docker-compose-ACS.yml)

2) Only APS (docker-compose-base.yml + docker-compose-APS.yml)

3) ACS and APS (docker-compose-base.yml + docker-compose-ACS.yml + docker-compose-ACS.yml + docker-compose-Proxy.yml)

Deployment 1 to 2 can run easily on a laptop with 16 GB RAM. Deployment 3 need a 32 GB Laptop or a strong VM in the cloud. I plan to setup a VM in the cloud.

### General informations:
* It generates volume data in the project directory /data for alf-repo_data, mysql_data and solr-data
* it generates logs in the project folder /logs for alfresco, mysql and share
* If you want to create ACS fresh again delete those folders!!

### URLs
ACS Deployment:
* localhost:80/ alfresco root
* localhost:80/alfresco
* localhost:80/share
* localhost:80/workspace
* localhost:80/phpldapadmin
* localhost:81 ui mail client

APS Deployment:
* localhost:80/acitiviti-app
* localhost:80/activiti-admin
* localhost:80/phpldapadmin
* localhost:81 ui mail client

### ACS Deployment
* For Linux and Mac you simply can use the following for starting the deployment
```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml up -d --build
```

or stopping it do:

```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml stop
```

And for tearing it down use:

```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml down
rm -rf data
rm -rf logs
```

### APS Deployment
* For Linux and Mac you simply can use the following for starting the deployment
```
docker-compose -f docker-compose-base.yml -f docker-compose-APS.yml up -d --build
```

or stopping it do:

```
docker-compose -f docker-compose-base.yml -f docker-compose-APS.yml stop
```

And for tearing it down use:

```
docker-compose -f docker-compose-base.yml -f docker-compose-APS.yml down
rm -rf data
rm -rf logs
```

### ACS + APS Deployment
**NOTICE** That is very memory expensive. Don't run the following if you not have more then 16GB Memory! \
**NOTICE** I will create an EC2 VM for this deployment

* For Linux and Mac you simply can use the following for starting the deployment
```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml -f docker-compose-APS.yml -f docker-compose-Proxy.yml up -d --build
```

or stopping it do:

```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml -f docker-compose-APS.yml -f docker-compose-Proxy.yml stop
```

And for tearing it down use:

```
docker-compose -f docker-compose-base.yml -f docker-compose-ACS.yml -f docker-compose-APS.yml -f docker-compose-Proxy.yml down
rm -rf data
rm -rf logs
```


<!-- * Windows User
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
``` -->
