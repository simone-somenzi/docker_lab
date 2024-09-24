# Docker examples

## Install Docker
~~~bash
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

#Add user to docker group

sudo usermod -aG docker $USER
~~~

## Working with containers

[Docker container commands](./docker-commands/docker-commands.md)

## Working with images

[Docker images examples](./docker-images/docker-images.md)

## Working with  volumes

[Docker volumes examples](./docker-volumes/docker-volumes.md)

## Working with docker compose

[Docker compose examples](./docker-compose/docker-compose.md)

