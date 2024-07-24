# App Deployment with Docker & K8s 

## Getting Started with Create React App

## Prerequisite

* NodeJs
* Docker
* Kubernetes

## what are Docker and Containers?

***Docker is a platform that uses containerization to allow developers to package applications and their dependencies into containers. Containers are lightweight, portable, and run consistently across different environments. Docker ensures that applications work seamlessly in development, testing, and production by providing an isolated environment for each application. This enhances scalability, efficiency, and collaboration in software development and deployment.***

## What is Kubernetes(K8s)?

***Kubernetes, often abbreviated as K8s, is an open-source platform designed for automating the deployment, scaling, and management of containerized applications. It orchestrates containers across a cluster of machines, providing tools for load balancing, scaling, and managing the lifecycle of applications. Kubernetes helps ensure that applications run reliably and efficiently by managing resources, monitoring system health, and enabling seamless updates and rollbacks. It is widely used for its ability to handle complex microservices architectures and large-scale production environments.***

### Practical Steps

1. Install all things which is given in Prerequisite 
2. Create Project Folder in VSCode
3. Create a react app

In the project directory, you can create react app using:

```
npx create-react-app kubetestapp
```

3. Runs the app using:
   
```
npm start
```

4. Delete node_modules file
5. Create Dockerfile

6. After Creating Dockerfile Create Docker Image using:

```
docker build -t xyz/demo-app:01 .
```

7. Push Created Docker image in our created repository in DockerHub using:

```
docker push xyz/demo-app:01
```

8. Now after pushing docker image in docker hub start our minikube(kubernetes) cluster using:

```
minikube start
```

9. Check minikube status using:

```
minikube status
```

10. now pull our created Docker Image

```
kubectl create deployment new-webapp --image=xyz/demo-app:01
```

11. Check our deployments and pods using:

```
kubectl get deployments
kubectl get pods
```
12. now expose our demo app on port number 3000

```
kubectl expose deployment newwebapp --type=LoadBalancer --port=3000
```

### with this above steps you can see your react app which is deploy with kubernetes

now,
## Updating our app [K8 Rollout]

* make changes in app
* build new docker image
* push newly created docker image in docker hub

now on kubernetes,
use command :
```
kubectl set image deployment newwebapp demo_webapp=xyz/demo-app:02
```
* in above command in "newwebapp" use your image name for update and in place of "demo_webapp" use your container name

step2:
```
kubectl get pods
```

* ### note: when you execute above command our old image is terminate and our new image is running  
