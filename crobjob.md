# Cronjob in Debian

Installing Cron and Crontab

```php
apt-get install cron
```

Opening crontab with a text editor

```php
crontab -e
```

Content of run.sh `Docker`

```php
#!/bin/bash
TODAY=`date +"%d%b%Y"`
DATEFILEDELETE=`date  -d "$date -7 days" +"%d%b%Y"`

docker exec --user root [container-name] mysqldump -u[username] -p[password] databasename > /[link-to-folder]/${TODAY}.sql

rm -rf /[link-to-folder]/${DATEFILEDELETE}.sql
```

Content of run.sh `Normally`

```php
#!/bin/bash
TODAY=`date +"%d%b%Y"`
DATEFILEDELETE=`date  -d "$date -7 days" +"%d%b%Y"`

mysqldump -u[username] -p[password] databasename > /[link-to-folder]/${TODAY}.sql

rm -rf /[link-to-folder]/${DATEFILEDELETE}.sql
```
