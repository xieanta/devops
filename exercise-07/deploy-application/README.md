# deploy-application

# Getting started

## Fast start

* Set up file .env in root of repository "deploy-application":
 ```sh
touch .env
```
* Copy the .env file from .env.example and include your values where necessary:
 ```sh
cp .env.example .env
```

* Build app with command:
```sh
docker compose up
```

* Enter in browser:
```sh
http://127.0.0.1:3000
```

# frontend
* docker build image from the root of frotend repository
```sh
docker build -t nzaitseva/frontend .
```
* docker push image from the 
root of frotend repository
```sh
docker image push nzaitseva/frontend
```
Link: https://hub.docker.com/r/nzaitseva/frontend/tags

# backend
* docker build image from the 
root of backend repository
```sh
docker build -t nzaitseva/
backend .
```
* docker push image from the 
root of frotend repository
```sh
docker image push nzaitseva/
backend
```
Link: https://hub.docker.com/r/nzaitseva/backend/tags