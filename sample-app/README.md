# Sample App

- https://qiita.com/YutaSaito1991/items/1a001f0e19e9de033612


## 実行方法

```
docker build -t sample-app:latest .
docker run --name sample-app -p 80:80 -d sample-app:latest
```

```
docker stop sample-app
docker rm sample-app
```
