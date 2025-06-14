# exercise-10



## Getting started

* Go to:
```sh
cd .deploy/k8s/kind
```
* Create cluster with command:
```sh
kind create cluster --config kind-cluster.yaml  
```
* Run Cloud Provider KIND in another terminal's tab:
```sh
cloud-provider-kind
```
* Go to:
```sh
cd ../helm
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
### Database
* Apply secrets-postgres:
```sh
kubectl apply -f secret-postgres.yaml -n workshop2024
```
* Set up external chart bitnami with your values:
```sh
helm install postgres oci://registry-1.docker.io/bitnamicharts/postgresql -f my_values_postgres.yaml -n workshop2024
```
Wait until pod is running.
### Backend
* Set up backend chart (template: helm install < your realease name> < path to chart> -n < your namespace>):
```sh
helm install backend backend -n workshop2024
```
Wait until pod is running.
### Frontend
* Set up frontend chart (template: helm install < your realease name> < path to chart> -n < your namespace>):
```sh
helm install frontend frontend -n workshop2024
```
Wait until pod is running.

### Settings
* Found out external ip of ingress controller service:
```sh
kubectl get svc -n ingress-nginx
```
* Add to /etc/hosts a new host:
```bash
<external-ip your ingress service controller> my-service.local
```
#### Now app is available on url:

#### my-service.local or http://my-service.local


If you want to delete pod:
1. For frontend

```bash
helm uninstall frontend -n workshop2024 
```
2. For backend

```bash
helm uninstall backend -n workshop2024 
```
3. For database

```bash
helm uninstall postgres -n workshop2024 

kubectl delete pvc data-postgres-postgresql-0 -n workshop2024

```