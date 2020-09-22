# AWS CloudFormation (ECS)

## aws cli のためのコマンド補完設定

```
echo "complete -C '/usr/local/bin/aws_completer' aws" >> ~/.bashrc
source ~/.bashrc
```

## CloudFormationの実行コマンド (VPC)

### dry run(changeset)

```
aws cloudformation deploy --stack-name demo-vpc --template-file ./vpc.yml --no-execute-changeset --profile demo
```

### deploy

```
aws cloudformation deploy --stack-name demo-vpc --template-file ./vpc.yml --profile demo
```

