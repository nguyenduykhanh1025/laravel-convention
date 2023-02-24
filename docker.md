# Docker

1. Build docker

```php
docker-compose build app
```

2. Run docker

```php
docker-compose up -d
```

3. List containers

```php
docker ps -a
```

4. Executed to a container

```php
docker exec -it [container-id] php artisan migrate --seed
```

5. Down docker

```php
docker-compose down
```

# Stop all containers

docker stop `docker ps -qa`

# Remove all containers

docker rm `docker ps -qa`

# Remove all images

docker rmi -f `docker images -qa `

# Remove all volumes

docker volume rm $(docker volume ls -qf)

# Remove all networks

docker network rm `docker network ls -q`

# Your installation should now be all fresh and clean.

# The following commands should not output any items:

# docker ps -a

# docker images -a

# docker volume ls

# The following command show only show the default networks:

# docker network ls
