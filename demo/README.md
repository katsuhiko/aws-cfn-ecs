# Sample App

- https://qiita.com/YutaSaito1991/items/1a001f0e19e9de033612


## 実行方法

```
docker build -t demo-app:latest .
docker run --name demo-app -p 80:80 -d demo-app:latest
```

```
docker stop demo-app
docker rm demo-app
```
