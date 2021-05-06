## Dockerise a React App and deploy on Minikube Kubernetes Cluster with rolling update from Dockerhub.


npm run-script build

docker build -t mrscottiefy/minikube-react-app:v1.2 .
docker push mrscottiefy/minikube-react-app:v1.2

kubectl get pods
kubectl describe pods | grep minikube-react-app
kubectl rollout restart deployment/minikube-react-app


