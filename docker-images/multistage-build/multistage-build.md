# Multi stage example

## Build image

~~~bash
docker build \
    -t no-multi \
    docker-images/multistage-build 
~~~

Check image size 

~~~bash
docker images no-multi
docker image inspect no-multi:latest
~~~

## Build multi-stage image

~~~bash
docker build \
    -t multi \
    -f docker-images/multistage-build/multi_Dockerfile .
~~~

Check image size 

~~~bash
docker images 

docker image inspect no-multi:latest --format='{{.RootFS.Layers}}' 
docker image inspect multi:latest --format='{{.RootFS.Layers}}' 

docker image inspect no-multi:latest | jq .[].RootFS
docker image inspect multi:latest | jq .[].RootFS
~~~



