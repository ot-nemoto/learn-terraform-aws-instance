# learn-terraform-aws-instance

-   [Terraform Tutorials AWS](https://developer.hashicorp.com/terraform/tutorials/aws-get-started)

## 事前準備

```sh
export AWS_ACCESS_KEY_ID=
export AWS_SECRET_ACCESS_KEY=
```

## コマンド

**ディレクトリを初期化**

```sh
terraform init
```

**構成をフォーマット**

```sh
terraform fmt
```

-   拡張機能に `esbenp.prettier-vscode`, `hashicorp.terraform` 設定済み
-   settings.json に `terraform`, `terraform-vars` の設定済み

**構成を検証**

```sh
terraform validate
```

**インフラストラクチャの作成**

```sh
terraform apply
```

**状態の確認**

```sh
terraform show
```

**リソース一覧**

```sh
terraform state list
```
