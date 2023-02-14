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
