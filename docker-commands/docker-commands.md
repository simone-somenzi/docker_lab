# Docker container commands 

Configure container name for testing
~~~bash
CONTAINER_NAME=mynginx
~~~

## Run with name
~~~bash
docker run \
    --name $CONTAINER_NAME \
    nginx
~~~

## Container list
~~~bash
docker ps 
#list stopped containers
docker ps -a
~~~


## Run and remove container when stopped
~~~bash
docker run \
    --rm \
    --name $CONTAINER_NAME \
    nginx
~~~

## Run in detached mode (background)
~~~bash
docker run \
    --rm \
    -d \
    --name $CONTAINER_NAME \
    nginx
~~~


## Stop - start - remove 
~~~bash
docker run \
    -d \
    --name $CONTAINER_NAME \
    nginx

docker stop  $CONTAINER_NAME 

docker start  $CONTAINER_NAME 

docker rm  $CONTAINER_NAME 

for i in {2..4}
do
    docker run --rm -d --name $CONTAINER_NAME$i nginx
done

#stop all running containers
docker stop $(docker ps -q)

#remove all stopped container
docker rm $(docker ps -qa)
~~~

## Reatart policy
-   unless-stopped 
- always
- on-failure

~~~bash
docker run \
    -d \
    --restart unless-stopped \
    --name $CONTAINER_NAME \
    nginx
~~~

## Pass evn variables
~~~bash
docker run \
    --rm \
    -d \
    --env ENV=production \
    --env LOG_LEVEL=info \
    --name $CONTAINER_NAME \
    nginx
~~~

## Execute command in running container
~~~bash
docker exec \
    $CONTAINER_NAME \
    ls
~~~

## Execute command in intercative mode
~~~bash
docker exec \
    -it \
    $CONTAINER_NAME \
    bash
~~~

## Copy file to a running container
~~~bash
docker cp \
    /etc/resolv.conf \
    $CONTAINER_NAME:/tmp
~~~


## Copy file from a running container
~~~bash
docker cp \
    $CONTAINER_NAME:/usr/share/nginx/html/index.html \
    /tmp 
~~~

## Container log
~~~bash
docker logs $CONTAINER_NAME -f
~~~

## Container stats
~~~bash
docker stats
~~~

## Port mapping
~~~bash
docker run \
    --rm \
    -d \
    --env ENV=production \
    --env LOG_LEVEL=info \
    --name $CONTAINER_NAME \
    -p 8080:80 \
    nginx
~~~

# Docker network

## Get network information
~~~bash
docker network inspect bridge
docker network inspect bridge | jq .[].Containers
~~~

## Create a network 
~~~bash
docker network create test-network
docker network inspect test-network
~~~

## Run container is host newtwork
~~~bash
docker run \
    --rm \
    -d \
    --network test-network \
    --name test-network-container \
    nginx
~~~

~~~bash
docker run \
    --rm \
    -d \
    -p 80:80 \
    --name test-network-container \
    nginx
~~~

## Create a network with specific subnet
~~~bash
docker network create test-subnet --subnet 192.168.200.0/24
~~~


~~~bash
docker run \
    --rm \
    -d \
    --network host \
    --name test-network-container \
    nginx
~~~

~~~bash
docekr network rm

docker network prune
~~~

## Get container network information
~~~bash
docker network ls
docker container inspect --format='{{.NetworkSettings.IPAddress}}' <container>
docker exec <container> tail -1 /etc/hosts
~~~

## Port mapping list
~~~bash
docker port $CONTAINER_NAME
~~~

