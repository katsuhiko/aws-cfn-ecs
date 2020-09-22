# AWS CloudFormation (ECS)

## aws cli のためのコマンド補完設定

```
echo "complete -C '/usr/local/bin/aws_completer' aws" >> ~/.bashrc
source ~/.bashrc
```

## CloudFormation ファイルの依存関係

- vpc.yml : なし
- sg.yml : vpc.yml
- ecr.yml : なし
- ecs-cluster.yml : なし
- ecs-service.yml : vpc.yml, sg.yml, ecr.yml, ecs-cluster.yml


## CloudFormationの実行コマンド (VPC)

### dry run(changeset)

```
aws cloudformation deploy --stack-name demo-vpc --template-file ./cfn/vpc.yml --no-execute-changeset --profile demo
```

### deploy

```
aws cloudformation deploy --stack-name demo-vpc --template-file ./cfn/vpc.yml --profile demo
```

```
aws cloudformation deploy --stack-name demo-ecs-service --template-file ./cfn/ecs-service.yml --capabilities CAPABILITY_NAMED_IAM --profile demo
```
