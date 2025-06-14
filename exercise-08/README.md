
# exercise-08



## Getting started
* Set up kind according the docs [installation guide for kind](https://kind.sigs.k8s.io/docs/user/quick-start/#installation):

    For MacOS:
```sh
brew install kind
```

* Make the cluster:
```sh
kind create cluster --config .deploy/k8s/kind/kind-cluster.yml
```
* Apply manifests:
```sh
kubectl apply -f .deploy/k8s/manifests/service.yaml && kubectl apply -f .deploy/k8s/manifests/deployment.yaml
```
* Check the manifests were applied and frontend pod is running:
```sh
kubectl get pods
kubectl get services
```
* Do port forward:
```sh
kubectl port-forward deployment.apps/frontend-deployment 3000:3000
```
Now you can open app a locally in browser:
```
127.0.0.1:3000/login
127.0.0.1:3000/register
```
* There is also run option by ingress by extraPortMapping:
```sh
kubectl apply -f https://kind.sigs.k8s.io/examples/ingress/deploy-ingress-nginx.yaml
```
* Check ingress controller works:
```sh
kubectl get pods -n ingress-nginx
```
* Apply manifest:
```sh
kubectl apply -f .deploy/k8s/manifests/ingress.yaml
```
* Check the ingress-nginx was applied:
```sh
kubectl get ingress
```
Now you can open app a locally in browser:
```
localhost:80/login
localhost:80/register
```

