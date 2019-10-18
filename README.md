# dotnetcore
Demo dot net core app

This is sample .net core app. Follow below steps to know how to build/push/run this application on local kubernetes cluster.

Pre-requisites:

a) Docker Desktop Community running. [Click here to install](https://docs.docker.com/docker-for-windows/install/)
b) Kubernetes should be enabled on Docker Desktop. Follow below link on how to enable kubernetes on docker desktop:
[Enable Kubernetes on Docker Desktop](https://docs.docker.com/docker-for-windows/#kubernetes)
c) Docker hub account and public repository.

## build the app

`docker build --tag <docker hub repo> -f .\dockerfile .`

e.g.,

`docker build --tag anubhavkul89/demodotnetcore -f .\Dockerfile .`

## push image to docker hub repo

`docker push <docker hub repo>`

e.g.,

`docker push anubhavkul89/demodotnetcore`

## run the app
`docker run -d -p 8080:80 --name webapp <docker hub repo>`

e.g.,

`docker run -d -p 8080:80 --name webapp anubhavkul89/demodotnetcore`

## run same app on local kubernetes cluster

To deploy app on local kubernetes cluster, run below command:

kubectl apply -f .\deploy.yaml
kubectl apply -f .\service.yaml

Execute below command to verify if pod is up and running

kubectl get pods

To see pod deployment description:

kubectl describe pods <pod name>
  
## Verify app is up and running

Once pod is up and running, trying hittng http://localhost:8080 and you should see your app running.



