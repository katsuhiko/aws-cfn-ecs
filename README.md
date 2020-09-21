# AWS CloudFormation (ECS)

## aws cli のためのコマンド補完設定

```
echo "complete -C '/usr/local/bin/aws_completer' aws" >> ~/.bashrc
source ~/.bashrc
```

## CloudFormationの実行コマンド (VPC)

### validate

```
aws cloudformation validate-template --template-body file://vpc.yml --profile demo
```

### create

```
aws cloudformation create-stack --stack-name demo-vpc --template-body file://vpc.yml --profile demo
```

### update

```
aws cloudformation update-stack --stack-name demo-vpc --template-body file://vpc.yml --profile demo
```

