# Symfony 4.* basic application skeleton includes:
- Docker (php + nginx + postgres + adminer + redis)
- Codeception 
- XDebug

##  Install Docker 

https://docs.docker.com/install/

### Installation on Ubuntu

https://docs.docker.com/install/linux/docker-ce/ubuntu/

```
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    software-properties-common
```

```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

```
sudo add-apt-repository \
       "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
       $(lsb_release -cs) \
       stable"
```

```
sudo apt-get update
```

```
sudo apt-get -y install docker-ce
```

## Create the docker group

```
sudo groupadd docker
sudo usermod -aG docker $USER
```

##  Install docker-compose 

https://docs.docker.com/compose/install/

### Installation on Ubuntu

```
sudo curl -L https://github.com/docker/compose/releases/download/1.19.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```

```
sudo chmod +x /usr/local/bin/docker-compose
```

##  Install docker-hostmanager

https://github.com/iamluc/docker-hostmanager

### Installation on Ubuntu

https://github.com/iamluc/docker-hostmanager#linux

```
docker run -d --name docker-hostmanager --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v /etc/hosts:/hosts iamluc/docker-hostmanager
```

##  Add ENV file

create .env file from .env.dist file and set correct vars values in it


##  Start with Docker

```
docker-compose up -d --build
```

##  run commands after setup


install composer libs
```
docker exec -it --user 1000 symfony4basicskeleton_php_1 composer install
```

run migrations
```
docker exec -it --user="www-data" symfony4basicskeleton_php_1 bin/console doctrine:migrations:migrate
```

where symfony4basicskeleton_php_1 php container name

## URLs:
"http://site.symfony4basicskeleton_local/" - website
"http://adminer.symfony4basicskeleton_local:8080/" - adminer