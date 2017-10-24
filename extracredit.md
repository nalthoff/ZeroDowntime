### Extra Credit - Kubernetes cluster

If you are up for it, get a Kubernetes cluster up and running, dockerize your app and push it to the cluster!

## Prerequisites
- [Docker](https://www.docker.com/get-docker)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- Azure CLI (Version 2.0.14-2)
- Docker Hub account [link](https://hub.docker.com/)

```
sudo apt-key adv --keyserver packages.microsoft.com --recv-keys 417A0893
sudo apt-get install apt-transport-https
sudo apt-get update && sudo apt-get install azure-cli=2.0.14-2
```

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

## Dockerize your app
1. Create a simple Web / API App
2. Click Add -> Docker Support
3. Validate code runs locally

## Push your new image to docker hub

[Blog Post](https://blog.codeship.com/using-docker-push-to-publish-images-to-dockerhub/)

## Create deployment
[Kubernetes docs](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- Use deployment.yaml file in this repo as a starting point
- Update yaml to point to your new docker hub image
