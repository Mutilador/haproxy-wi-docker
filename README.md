# ENVs


**MYSQL_ENABLE** - the default is 0 ( disabled, use SQLITE ) turn on change to 1 

**MYSQL_USER** - the default is "haproxywi"

**MYSQL_PASS** - the default is "haproxywi"

**MYSQL_DB** - the default is "haproxy-wi"

**MYSQL_HOST** - the default is 127.0.0.1


### For MySQL support:
```
MariaDB [(none)]> create user 'haproxy-wi'@'%';
MariaDB [(none)]> create database haproxywi;
MariaDB [(none)]> grant all on haproxywi.* to 'haproxy-wi'@'%' IDENTIFIED BY 'haproxy-wi';
MariaDB [(none)]> grant all on haproxywi.* to 'haproxy-wi'@'localhost' IDENTIFIED BY 'haproxy-wi';
```

# Docker
```
docker service create --detach=false --name haproxy-wi -e MYSQL_ENABLE=1 -e MYSQL_USE="haproxywi" -e MYSQL_PASS="haproxywi" --mount type=volume,src=haproxy-wi,dst=/var/www/haproxy-wi/app -p 8080:80 mbnunes/haproxy-wi-docker-envs
```
or
```
docker run -d --name haproxy-wi -v haproxy-wi:/var/www/haproxy-wi/app -p 8080:80 mbnunes/haproxy-wi-docker-envs
```
# OS support
HAProxy-WI was tested on EL 7, and all scripts too. Debian/Ubuntu OS support at 'beta' stage, may work not correct

# Database support

Default Haproxy-WI use Sqlite, if you want use MySQL enable in config, and create database:


