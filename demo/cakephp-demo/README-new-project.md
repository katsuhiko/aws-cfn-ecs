# New Project

## CakePHP プロジェクトの作成

```
cd .
docker run --rm -it -v "$(pwd):/home/app" -w /home/app katsuhikonagashima/php-fpm-base:7.4-buster /bin/bash
```

```
curl -sS https://getcomposer.org/installer | php

php composer.phar create-project --prefer-dist cakephp/app:4.* cakephp-demo
cp composer.phar ./cakephp-demo/
mv composer.phar ./cakephp-demo/
exit
```


## Docker の準備

docker-compose を動かすためのファイルを用意

- ./docker-compose.yml の作成
- ./docker/local/ 配下の各種ファイルの作成
- ./docker/server/ 配下の各種ファイルの作成
- ./config/app_local.php, app_local.example.php のDB接続情報を変更
- ./config/app.php のログ出力を標準出力へ変更
- ./config/app.php のSession設定を Database へ変更
