### Extra Credit - Kubernetes cluster

If you are up for it, get a Kubernetes cluster up and running, dockerize your app and push it to the cluster!

## Prerequisites
- [Docker](https://www.docker.com/get-docker)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Dockerize your app

## Create a kubernetes cluster via ACS

run the following commands in a bash shell to create a kubernetes cluster in Azure
```

az login

rgname=zerodowntime_acs
acs_name=zerodowntimeacs
az group create --name $rgname --location southcentralus

az acs create --orchestrator-type=kubernetes \
    --resource-group $rgname \
    --name=$acs_name \
    --generate-ssh-keys \
	--admin-password=P@ssword123!

az acs kubernetes get-credentials --resource-group=$rgname --name=$acs_nam
```

## Push your code to docker hub

[Blog Post](https://blog.codeship.com/using-docker-push-to-publish-images-to-dockerhub/)

## Create deployment
[Kubernetes docs](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)