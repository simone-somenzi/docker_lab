# Docker Volume

## Cow in writable layer
~~~bash
docker run  \
    --rm \
    -d \
    --name busybox \
    busybox  \
    sleep infinitely

# get container size
docker ps -s

#copy file in the container
docker cp \
    /etc/resolv.conf \
    busybox:/tmp

# get container size
docker ps -s
~~~


## Host volume 

~~~bash
HOST_FOLDER=/tmp/mount/mynginx-host-volume
CONTAINER_NAME=mynginx-host-volume
 
docker run \
    --rm \
    -d \
    --name $CONTAINER_NAME \
    -v $HOST_FOLDER:/usr/share/nginx/html/mynginx-volume \
    nginx

sudo cp docker-images/mynginx/image/{aifactory.svg,index.html} $HOST_FOLDER

docker container inspect --format='{{.NetworkSettings.IPAddress}}' $CONTAINER_NAME
~~~

## Anonymous volume 

~~~bash
CONTAINER_NAME=mynginx-anonymous-volume

docker run \
    --rm \
    -d \
    --name $CONTAINER_NAME  \
    -v /usr/share/nginx/html/mynginx-volume \
    nginx

docker volume ls

sudo ls /var/lib/docker/volumes/ -ltr

sudo cp docker-images/mynginx/image/{aifactory.svg,index.html}  $(docker container inspect $CONTAINER_NAME | jq -r .[].Mounts[0].Source)

docker container inspect --format='{{.NetworkSettings.IPAddress}}' $CONTAINER_NAME 
~~~


## Named volume 

~~~bash
CONTAINER_NAME=mynginx-named-volume

docker run \
    --rm \
    -d \
    --name $CONTAINER_NAME  \
    -v $CONTAINER_NAME:/usr/share/nginx/html/mynginx-volume \
    nginx

docker volume ls

sudo ls /var/lib/docker/volumes/ -ltr

sudo cp docker-images/mynginx/image/{aifactory.svg,index.html} $(docker container inspect $CONTAINER_NAME | jq -r .[].Mounts[0].Source)

docker container inspect --format='{{.NetworkSettings.IPAddress}}' $CONTAINER_NAME 

docker container inspect $CONTAINER_NAME | jq .[].Mounts
~~~

