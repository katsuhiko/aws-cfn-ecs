# CakePHP Demo


## インストール

```
cd cakephp-demo

cp ./config/.env.example ./config/.env
cp ./config/app_local.example.php ./config/app_local.php

docker-compose up -d
docker exec -it app php composer.phar install
docker exec -it app bin/cake migrations migrate

docker exec -it app php composer.phar check
```
