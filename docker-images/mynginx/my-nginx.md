# Mynginx example

## Build image

~~~bash
echo "Building image $IMAGE_TAG ..."

source docker-images/mynginx/set_env_variables.sh

docker build \
    -t $REGISTRY/$IMAGE_NAME:$IMAGE_TAG \
    docker-images/mynginx/image
~~~

## Run container 

~~~bash
docker run \
    -it \
    --rm \
    -d \
    --name mynginx \
     $REGISTRY/$IMAGE_NAME:$IMAGE_TAG
~~~

## Push image to registry

~~~bash
echo "Pushing image $IMAGE_TAG ..."

docker push $REGISTRY/$IMAGE_NAME:$IMAGE_TAG 
~~~

## Pull image from registry

~~~bash
echo "Pushing image $IMAGE_TAG ..."

docker pull $REGISTRY/$IMAGE_NAME:$IMAGE_TAG 
~~~

