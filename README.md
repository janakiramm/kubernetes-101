# kubernetes-101
Tutorial to build and deploy a simple Python app in Kubernetes. The walkthrough is available [here](https://youtu.be/zeS6OyDoy78).

Make sure that you have access to a Kubernetes cluster.

## Build a Docker image from existing Python source code and push it to Docker Hub. Replace DOCKER_HUB_USER with your Docker Hub username.
```
cd Docker
docker build -t <DOCKER_HUB_USER>/web .
docker push <DOCKER_HUB_USER>/web
```

## Launch the app with Docker Compose
```
docker-compose up -d 
```

## Test the app
```
curl localhost:5000
```

## Deploy the app to Kubernetes
```
cd ../Kubernetes
kubectl create -f db-pod.yml
kubectl create -f db-svc.yml
kubectl create -f web-pod.yml
kubectl create -f web-svc.yml
kubectl create -f web-rc.yml
```

## Check that the Pods and Services are created
```
kubectl get pods
kubectl get svc
```

## Get the NodePort for the web Service. Make a note of the port.
```
kubectl describe svc web
```

## Test the app by accessing the NodePort of one of the nodes.

```
kubectl get nodes
curl <NODE_IP>:<NODEPORT>
```









