# Memo

## テンプレートの設定項目
以下の項目からテンプレートを作る。

- AWSTemplateFormatVersion
  - テンプレートのバージョン、2020/07現在`2010-09-09`しかない。
- Description
  - 読む人用の説明
- Parameters
  - スタック作成時にパラメータとして引数を渡せる。
  - テンプレート内で`Ref`関数から参照値として扱える。
- Mappings
  - ハッシュ。key-valueでなにか設定したいときに。
- Conditions
  - 条件分岐。
- Resources
  - 作成するAWSリソース。
- Outputs
  - テンプレートで生成した結果を出力させる。
  - VPCのIDやEC2のIPアドレスなどに使うことが多い。
