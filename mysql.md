# Mysql

### Enable show log

```php
 CREATE TABLE `general_log` (
   `event_time` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP
                          ON UPDATE CURRENT_TIMESTAMP,
   `user_host` mediumtext NOT NULL,
   `thread_id` bigint(21) unsigned NOT NULL,
   `server_id` int(10) unsigned NOT NULL,
   `command_type` varchar(64) NOT NULL,
   `argument` mediumtext NOT NULL
  ) ENGINE=CSV DEFAULT CHARSET=utf8 COMMENT='General log'
```

```php
SET global general_log = 1;
SET global log_output = 'table';
select * from mysql.general_log;
```

### Grant role

1. Grant table role

```php
GRANT ALL PRIVILEGES ON [table-name].* TO '[username]'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```

2. Grant all role for root user

```php
GRANT ALL PRIVILEGES ON . TO root@'%';
FLUSH PRIVILEGES;
```

### Create user for grant

```php
GRANT ALL PRIVILEGES ON *.* TO 'daniel'@'10.10.10.10' WITH GRANT OPTION;
```
