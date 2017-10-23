### Extra Credit - Kubernetes cluster

If you are up for it, get a Kubernetes cluster up and running, dockerize your app and push it to the cluster!

## Prerequisites
- [Docker](https://www.docker.com/get-docker)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Dockerize your app

## Create a kubernetes cluster via ACS

az group create --name k8s --location southcentralus
az acs create --orchestrator-type=kubernetes \
    --resource-group k8s \
    --name=mywinK8s \
    --generate-ssh-keys \
    --windows \
    --admin-password=P@ssword123!

az acs kubernetes get-credentials --resource-group=k8s --name=mywink8s
az group delete -n k8s -y --no-wait

## Push your code to docker hub

[Blog Post](https://blog.codeship.com/using-docker-push-to-publish-images-to-dockerhub/)

## Create deployment
[Kubernetes docs](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)