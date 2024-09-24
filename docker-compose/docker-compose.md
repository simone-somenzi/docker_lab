# Docker Compose

Configure compose path for testing
~~~bash
#compose file
COMPOSE_FILE=docker-compose.yaml

#mongo example
COMPOSE_PATH=./docker-compose/mongo/
CONTAINER_NAME=mongo-express

#postgres example
COMPOSE_PATH=./docker-compose/postgres/
~~~

## Run Command
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE up
~~~

## Run in detached mode (background)
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  up -d
~~~

## List container in compose
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE ps 
~~~

## Stop - start - remove 
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  stop
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  start
~~~

## Stop - start - remove single container
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  stop $CONTAINER_NAME
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  start $CONTAINER_NAME
~~~

## Execute command in running container
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE exec $CONTAINER_NAME env
~~~

## Merge compose file
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE -f $COMPOSE_PATH/compose-dev-override.yaml  up -d

docker compose -f $COMPOSE_PATH/$COMPOSE_FILE -f $COMPOSE_PATH/compose-prod-override.yaml  up -d
~~~


## Compose log
~~~bash
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  logs
docker compose -f $COMPOSE_PATH/$COMPOSE_FILE  logs $CONTAINER_NAME
~~~



