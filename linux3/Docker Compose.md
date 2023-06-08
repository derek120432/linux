```
mkdir test-dockerfile
gedit Dockerfile
cd test-dockerfile
touck "110910514李韋德" > index.html
```

Dockerfile

```
FROM centos:7.9.2009
RUN yum -y install httpd
EXPOSE 80
ADD index.html /var/www/html
```

執行Dockerfile

```
docker build -t derek:httpd .
docker run -d -p 8888:80 derek:httpd /usr/sbin/apachectl -DFOREGROUND
```



***

## Docker Compose

```
mkdir docker-compose
cd docker-compose
vim docker-compose.yml
```

##### docker-compose.yml

```
version: '3'
services:
  web:
    image: "derek:httpd"
    ports:
      - "8899:80"
    command: "usr/sbin/apachectl -DFOREGROUND"

```

docker-compose執行(一定要在資料夾底下)

```
docker-compose up -d #-d在背景執行
docker-compose ps
docker-compose down
```



***

## jumpserver

帳號:admin

密碼:derek3322

```
```

