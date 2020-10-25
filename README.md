# AWS CloudFormation (ECS)

## aws cli のためのコマンド補完設定

```
echo "complete -C '/usr/local/bin/aws_completer' aws" >> ~/.bashrc
source ~/.bashrc
```

## CloudFormation ファイルの依存関係

- route53.yml : なし

- vpc.yml : なし
- sg.yml : vpc.yml

- alb.yml : route53.yml, vpc.yml, sg.yml
- aurora-mysql.yml : vpc.yml, sg.yml

- ecr.yml : なし
- ecs-cluster.yml : なし
- ecs-service.yml : vpc.yml, sg.yml, ecr.yml, ecs-cluster.yml, alb.yml, aurora-mysql.yml (route53.yml)

- alarm-base.yml : なし
- alarm-ecs-service.yml : alarm-base.yml, alb.yml, ecs-service.yml


## CloudFormationの実行コマンド (VPC)

### dry run(changeset)

```
aws cloudformation deploy --stack-name demo-vpc --template-file ./cfn/vpc.yml --no-execute-changeset --profile demo
```

### deploy

```
# --notification-arns arn:aws:sns:ap-northeast-1:99999999999:demo-notification-topic
#
# export TOPIC=$(aws sns list-topics --query 'Topics[?contains(TopicArn,`notification`)].TopicArn' --output text --profile demo)
# --notification-arns $TOPIC

aws cloudformation deploy --stack-name demo-route53 --template-file ./cfn/route53.yml --profile demo --parameter-overrides ZoneName=demo.example.com
※ ドメインの条件により、AWS管理コンソールの Certificate Manager から「Route 53 でのレコードの作成」を行わないといけない。

aws cloudformation deploy --stack-name demo-vpc --template-file ./cfn/vpc.yml --profile demo
aws cloudformation deploy --stack-name demo-sg --template-file ./cfn/sg.yml --profile demo

aws cloudformation deploy --stack-name demo-alb --template-file ./cfn/alb.yml --profile demo
aws cloudformation deploy --stack-name demo-aurora-mysql --template-file ./cfn/aurora-mysql.yml --profile demo

aws cloudformation deploy --stack-name demo-ecr --template-file ./cfn/ecr.yml --profile demo
aws cloudformation deploy --stack-name demo-ecs-cluster --template-file ./cfn/ecs-cluster.yml --profile demo
aws cloudformation deploy --stack-name demo-ecs-service --template-file ./cfn/ecs-service.yml --capabilities CAPABILITY_NAMED_IAM --profile demo

aws cloudformation deploy --stack-name demo-alarm-base --template-file ./cfn/alarm-base.yml --capabilities CAPABILITY_NAMED_IAM --profile demo --parameter-overrides WorkspaceId=ABCDE1234 NotificationChannelId=ABCDE1234 AlarmChannelId=ABCDE1234
※ AWS管理コンソールの Chatbot から「新しいクライアントを設定」を行い、Slack と連携しておく。
aws cloudformation deploy --stack-name demo-alarm-ecs-service --template-file ./cfn/alarm-ecs-service.yml --profile demo
```
