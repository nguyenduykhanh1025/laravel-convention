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

6 Stop all containers

```php
docker stop `docker ps -qa`
```

7 Remove all containers

```php
docker rm `docker ps -qa`
```

8 Remove all images

```php
docker rmi -f `docker images -qa
```

9 Remove all volumes

```php
docker volume rm $(docker volume ls -q)
```

10 Remove all networks

```php
docker network rm `docker network ls -q`
```

11. List images

```php
docker images -a
```

12. List volumes

```php
docker volume ls
```
