# Docker images examples

## Mynginx example

[Mynginx example](./mynginx/my-nginx.md)

## Azure cli example

[Azure clie example](./azure-cli/azure-cli.md)

## Multi-stage build

[Multi-stage build example](./multistage-build/multistage-build.md)

## Working  with images
https://docs.docker.com/reference/cli/docker/image/ls/

List images
~~~bash
docker images
docker image ls
docekr image nginx
~~~

List and delete untagged images
~~~bash
docker images --filter "dangling=true"
docker rmi $(docker images -f "dangling=true" -q)
~~~

Delete builder layer
~~~bash
docker builder prune
~~~

Image history
~~~bash
docker image history <imagename>
docker image history nginx:latest
~~~

Image inspect
~~~bash
docker image inspect <imagename>
docker image inspect nginx:latest
~~~

Remove all images
~~~bash
 docker rmi $(docker images -q)
~~~


## Working with registry

Pull image
~~~bash
docker pull nginx
~~~

Tag image
~~~bash
docker tag  nginx innovationlabzucchetti.azurecr.io/zhc/nginx:v1.0.0
~~~

Docker registry login
~~~bash
docker login -u zhc-demo innovationlabzucchetti.azurecr.io
~~~

Push image
~~~bash
docker push innovationlabzucchetti.azurecr.io/zhc/nginx:v1.0.0
~~~

