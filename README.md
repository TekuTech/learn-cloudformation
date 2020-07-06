# learn-cloudformation

## CloudFormationとは
yml(json)形式でテンプレートを作成すると、設定項目をもとにリソースを作成してくれるサービス。
作成されるリソースの塊はスタックと呼ばれ、その単位で管理される。
構成をコードで管理できる(Infrastructure as a Code)ため、使いまわしが可能だったり、差分が発生した場合も管理しやすい。

## Usage
`100_vpc_sample.yml`はVPCとSubnetを作成するだけの簡単なテンプレート。
実行前にAWS-CLIを使用できるようにしておくこと。

### スタックに関する操作

#### create-stack
以下のコマンドでスタックを作成できる。
オプションはすべて必須、`--template-body`は`file://`で始めないといけないので注意。

```sh
aws cloudformation create-stack --stack-name sample-stack --region ap-northeast-1 --template-body file://100_vpc_sample.yml
```

#### describe-stacks / list-stacks
`describe-stacks`でスタックの情報を表示できる。

```sh
aws cloudformation describe-stacks --stack-name sample-stack
```

`list-stacks`で、現在のアカウントが作成したスタックの一覧を表示できる。

```sh
aws cloudformation list-stacks
```

#### update-stack
既存のスタックに変更が必要になった際は、テンプレートを変更して以下のコマンドを実行する。
スタックのステータスがUPDATE_IN_PROGRESSになり、追加されればOK。
テンプレートにスタックを書き忘れた際は削除されてしまうので注意！

```sh
aws cloudformation update-stack --stack-name sample-stack --template-body file://100_vpc_sample.yml 
```

### Templateに対する操作

#### validate-template
テンプレートの文法ミスがないかの確認コマンド。

```sh
aws cloudformation validate-template --template-body file://100_vpc_sample.yml 
```
