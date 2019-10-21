# dotnetcore
Demo dot net core app

This is sample .net core app. Follow below steps to know how to build/push/run this application on local kubernetes cluster.

Pre-requisites:

a) Docker Desktop Community running. [Click here to install](https://docs.docker.com/docker-for-windows/install/)

b) Kubernetes should be enabled on Docker Desktop. Follow below link on how to enable kubernetes on docker desktop:
[Enable Kubernetes on Docker Desktop](https://docs.docker.com/docker-for-windows/#kubernetes)

c) Docker hub account and public repository.

## 1. build the app

`docker build --tag <docker hub repo> -f .\dockerfile .`

e.g.,

`docker build --tag anubhavkul89/demodotnetcore -f .\Dockerfile .`

## 2. push image to docker hub repo

`docker push <docker hub repo>`

e.g.,

`docker push anubhavkul89/demodotnetcore`

## 3. run the app
`docker run -d -p 8080:80 --name webapp <docker hub repo>`

e.g.,

`docker run -d -p 8080:80 --name webapp anubhavkul89/demodotnetcore`


## 4. run same app on local kubernetes cluster

Before deploying app on K8 cluster, update the docker hub repository path in deploy.yaml file.

To deploy app on local kubernetes cluster, run below command:

`kubectl apply -f .\demodotnetcore\deploy.yaml`

To expose public IP address, run below comand:

`kubectl apply -f .\demodotnetcore\service.yaml`

Note: Since you are running K8s on your local laptop, you can access website on localhost.

Execute below command to verify if pod is up and running

`kubectl get pods`

Execute below commands to verify of service is up and running exposing public IP:

`kubectl get svc`

To see pod deployment description:

`kubectl describe pods <pod name>`
  
## 5. Verify app is up and running

Once pods and services are up and running, try hittng http://localhost and you should see your app running.



