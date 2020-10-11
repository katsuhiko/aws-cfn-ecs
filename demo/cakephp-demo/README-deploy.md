# (参考) デプロイ用 Dockerイメージの作成と動作確認

滅多にしない作業だけど、AWS環境へデプロイ後、動作しなくて原因がわからない場合、以下の手順でローカル環境で確認することもできます。

./docker/server/nginx/default.conf の `fastcgi_pass 127.0.0.1:9000;` を `fastcgi_pass app:9000;` へ変更してから実施してください。

```
cd cakephp-demo

# DockerImage の作成
docker build -t cakephp-demo-app -f ./docker/server/php-fpm/Dockerfile .
docker build -t cakephp-demo-web -f ./docker/server/nginx/Dockerfile .

# DB はデプロイ対象ではないので、ローカル開発用のDBを起動
docker-compose up -d db

# 作成した DockerImage を起動
docker run -d --name app --link db:db --net backend --env DEBUG=false cakephp-demo-app
docker run -d --name web --link app:app --net backend -p 80:80 cakephp-demo-web

# 確認が終わったら停止
docker stop web; docker rm web
docker stop app; docker rm app
docker-compose down
```
