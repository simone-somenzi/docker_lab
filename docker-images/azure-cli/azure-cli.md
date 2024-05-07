# Azure cli example

## Build image

~~~bash
docker build -t azurecli:v1.0.0  docker-images/azure-cli/
~~~

## Run container with default entrypoint and command

~~~bash
docker run --rm  --name azurecli azurecli:v1.0.0
~~~

## Run container with default entrypoint and different command

~~~bash
docker run --rm  --name azurecli azurecli:v1.0.0 login
~~~

## Run container with different entrypoint

~~~bash
docker run --rm --entrypoint tree --name  azurecli azurecli:v1.0.0 
docker run --rm  -it --entrypoint bash --name  azurecli azurecli:v1.0.0 
~~~