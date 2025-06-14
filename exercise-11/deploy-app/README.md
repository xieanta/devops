# deploy-app



## Getting started

* Go to:
```sh
cd .deploy/kind
```
* Add address your machine in kind-cluster.yaml:
```
apiServerAddress: <your ip-address>
```
* Create cluster with command:
```sh
kind create cluster --config kind-cluster.yaml  
```
* Go to:
```sh
cd ../manifests
```
* Create namespace:
```sh
kubectl apply  -f namespace.yaml
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
* Add group variables in UI GitLab:
```sh
DOCKER_HUB_USERNAME: <your username> # marked as Masked, Expanded
DOCKER_HUB_PASSWORD: <your password> # marked as Masked, Expanded
KUBECONFIG_FILE: <your encoded kubeconfig file> # cat ~/.kube/config | base64 # marked as Masked
```
* Go to:
```sh
cd ../..
```
* Create gitlab runners for frontend(frontend tag) and backend(backend tag).\
Set up field "runnerRegistrationTokenin" in files "gitlab_runner_backend.yml" and "gitlab_runner_frontend.yml" with values that were generated when creating gitlab runners.

* Start runner for backend
```sh
helm install gitlab-runner-backend gitlab/gitlab-runner -f gitlab-runner-backend.yml --create-namespace -n gitlab-runner
```
* Start runner for frontend
```sh
helm install gitlab-runner-frontend gitlab/gitlab-runner -f gitlab-runner-frontend.yml --create-namespace -n gitlab-runner
```
First start your backend pipeline and then frontend pipeline. Before running frontend pipeline take a few steps to have a settings for the application to work correctly.

### Settings before rinning frontend pipeline
* Run Cloud Provider KIND in another terminal's tab:
```sh
cloud-provider-kind
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