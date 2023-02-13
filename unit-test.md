# UNIT TEST CONFIG AND RUN

## Config

1. Run the following command in a terminal\

```php
php -i
```

![PHP -i](assets/php-i.PNG)

2. Copy the output of that command and paste it in the [Xdebug Wizard ][xdebug-wizard]. Then click Analyze my phpinfo() output.
   [xdebug-wizard]: https://xdebug.org/wizard
   ![xdebug-wizard](assets/xdebug-wizard.PNG)

3. Once analyzed, the result will tell if you have Xdebug installed or not, and which .dll file to download
   ![xdebug-dowload](assets/xdebug-dowload.PNG)

4. Move the downloaded file to the /ext folder. This is the folder where PHP keeps all of its extensions and can be found under the folder where you have installed PHP. On mine, it is located in C:\PHP\ext.
   ![xdebug-move-file](assets/xdebug-move-file.PNG)
5. Open php.ini file in an editor like Notepad, Notepad++ or Visual Code. This file is located within the folder where you installed PHP, C:\PHP\php.ini for me.
   ![xdebug-php-init](assets/xdebug-php-init.PNG)
6. Check if Xdebug has been installed by running the following command in a terminal

```php
php -v
```

![xdebug-check-version](assets/xdebug-check-version.PNG)

## Run unit test

```php
php artisan test --coverage
```

![php-run-unit-test](assets/php-run-unit-test.PNG)
