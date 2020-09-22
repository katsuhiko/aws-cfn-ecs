# AWS CloudFormation Command

## CloudFormationの実行コマンド

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

