# learn-terraform-aws-instance

-   [Terraform Tutorials AWS](https://developer.hashicorp.com/terraform/tutorials/aws-get-started)

## 事前準備

```sh
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=
```

## コマンド

### ディレクトリを初期化

```sh
terraform init
```

### 構成をフォーマット

```sh
terraform fmt
```

_vscode_

-   [拡張機能](.devcontainer/devcontainer.json)に `esbenp.prettier-vscode`, `hashicorp.terraform` 設定済み
-   [settings.json](.vscode/settings.json) に `terraform`, `terraform-vars` の設定済み

### 構成を検証

```sh
terraform validate
```

### インフラストラクチャの更新内容確認

```sh
terraform plan
```

### インフラストラクチャの作成

```sh
terraform apply
```

**変数のオーバーライド**

```sh
terraform apply -var "instance_name=YetAnotherName"
```

### 状態の確認

```sh
terraform show
```

### リソース一覧

```sh
terraform state list
```

### 出力値を表示

```sh
terraform output
```

### インフラストラクチャの削除

```sh
terraform destroy
```

## バリデーション

Amazon EC2 インスタンスが AWS Systems Manager の管理対象になっているか確認する

```sh
aws ssm start-automation-execution \
  --document-name "AWSSupport-TroubleshootManagedInstance" \
  --parameters '{"InstanceId":["i-052aed696b43c7e49"]}'
  # {
  #     "AutomationExecutionId": "8779d17e-0f0c-41a3-b3d7-feddaed8643c"
  # }
```

```sh
aws ssm get-automation-execution \
  --automation-execution-id "8779d17e-0f0c-41a3-b3d7-feddaed8643c" \
  --query 'AutomationExecution.StepExecutions[?StepName==`FinalOutput` && StepStatus==`Success`].Outputs.Message' \
  --output text
  # EC2 instance is managed by Systems Manager.
```
