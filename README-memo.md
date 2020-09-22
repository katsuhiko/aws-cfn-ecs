# AWS CloudFormation


## VSCode で AWS CloudFormation(YAML) を作成する環境を整備

- https://nopipi.hatenablog.com/entry/2019/04/27/155616


## お名前.com で取得したドメインに対してRoute53でサブドメインだけ管理する方法

- http://developersnote.jp/aws/route53.html


## CloudFormationの実行コマンド(非推奨!?)

基本は deploy コマンドを使うほうが良いみたい。

- https://dev.classmethod.jp/articles/aws-all-iac/#toc-11


### validate

```
aws cloudformation validate-template --template-body file://vpc.yml --profile demo
```

```
aws cloudformation create-stack --stack-name demo-vpc --template-body file://vpc.yml --profile demo
```

### create

```
aws cloudformation create-stack --stack-name demo-vpc --template-body file://vpc.yml --profile demo
```

### update

```
aws cloudformation update-stack --stack-name demo-vpc --template-body file://vpc.yml --profile demo
```


## ECR への Image プッシュ

```
cd demo

aws ecr get-login-password --region ap-northeast-1 --profile demo | docker login --username AWS --password-stdin XXXXXXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com
docker build -t demo-app:latest .
docker tag demo-app:latest XXXXXXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com/demo-app:init
docker push XXXXXXXXXXXX.dkr.ecr.ap-northeast-1.amazonaws.com/demo-app:init
```
