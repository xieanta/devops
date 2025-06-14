# exercise-09



## Getting started

* Go to:
```sh
cd .deploy/k8s/kind
```
* Create cluster with command:
```sh
kind create cluster --config kind-cluster.yaml --name=kind
```
* Run Cloud Provider KIND in another terminal's tab:
```sh
cloud-provider-kind
```
* Go to:
```sh
cd ../manifests
```
* Create namespace:
```sh
kubectl apply  -f namespace.yaml
```
* Apply ingress controller:
```sh
kubectl apply -f https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml
```
* Wait until is ready by command:
```sh
kubectl wait --namespace ingress-nginx \
  --for=condition=ready pod \
  --selector=app.kubernetes.io/component=controller \
  --timeout=90s
```
* Apply ingress manifest:
```sh
kubectl apply  -f ingress-fe.yaml -n workshop2024 
```
* Found out external ip of ingress controller service:
```sh
kubectl get svc -n ingress-nginx
```
* Add to /etc/hosts a new host:
```bash
<external-ip your ingress service controller> my-service.local
```
### Database:
1. Apply persistent-volume.yaml:
```sh
kubectl apply  -f persistent-volume.yaml -n workshop2024 
```
2. Apply persistent-volume-claim.yaml:
```sh
kubectl apply  -f persistent-volume-claim.yaml -n workshop2024 
```
3. Apply service-postgres.yaml
```sh
kubectl apply  -f service-postgres.yaml -n workshop2024 
```
4. Apply configmap-postgres.yaml
```sh
kubectl apply  -f configmap-postgres.yaml -n workshop2024 
```
5. Apply secret-postgres.yaml
```sh
kubectl apply  -f secret-postgres.yaml -n workshop2024 
```
6. Apply statefulset-postgres.yaml
```sh
kubectl apply  -f statefulset-postgres.yaml -n workshop2024 
```
Wait until pod is running.
### Backend:
1. Apply secret-be.yaml
```sh
kubectl apply  -f secret-be.yaml -n workshop2024 
```
2. Apply statefulset-be.yaml
```sh
kubectl apply  -f configmap-be.yaml -n workshop2024 
```
3. Apply service-be.yaml
```sh
kubectl apply  -f service-be.yaml -n workshop2024 
```
6. Apply deployment-be.yaml
```sh
kubectl apply  -f deployment-be.yaml -n workshop2024 
```
Wait until pod is running.
### Frontend:
1. Apply service-fe.yaml
```sh
kubectl apply  -f service-fe.yaml -n workshop2024 
```
2. Apply deployment-fe.yaml
```sh
kubectl apply  -f deployment-fe.yaml -n workshop2024 
```
Wait until pod is running.

#### Now app is available on url:

#### my-service.local or http://my-service.local