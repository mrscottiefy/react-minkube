## Dockerise a React App to Dockerhub 
## Deploy the React App on a local Minikube Kubernetes Cluster 
## Apply a rolling update on existing deployment/pods from Dockerhub.

### Create a React App  
``` 
cd <to workspace>
npx create-react-app react-minikube
```
### Build React App  
`npm run-script build`

### Build Docker Image, Tag (with version) and Push to Dockerhub
```
docker build -t mrscottiefy/minikube-react-app:v1.2 .
docker push mrscottiefy/minikube-react-app:v1.2
```

### Setup Minikube and Deploy Pods
```
minikube start
kubectl apply -f deployment.yaml
minikube service minikube-react-app
```

### Rolling updates to pods and automatically fetch latest image from Dockerhub
#### Verify pods lifespan and status
```
kubectl get pods
kubectl describe pods | grep minikube-react-app
kubectl rollout restart deployment/minikube-react-app
kubectl get pods
```

