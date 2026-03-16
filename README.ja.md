# 越前市ハザードマップ

越前市のオープンデータ（避難所、AED、医療機関など）を使用したWebベースのハザードマップです。

## 利用例

- [越前市ハザードマップ](https://code4fukui.github.io/echizencity-hazardmap/)

## 市区町村ハザードマップテンプレート

本プロジェクトでは、「[市区町村ハザードマップテンプレート](https://github.com/sankichi92/shikuchoson-hazardmap-template)」を活用しています。

このテンプレートは、[Tokyo OSS Party!! 2021](https://tokyo-oss-party.com/)の成果物で、Webベースの市区町村ハザードマップを容易に作成・公開できるようにするものです。

## 背景と課題

日本のハザードマップは国が管理する[ハザードマップポータルサイト](https://disaportal.gsi.go.jp/)にまとめられていますが、市区町村が独自に作成したハザードマップの詳細を確認するのが難しい状況でした。

このテンプレートは、市区町村がWebベースのハザードマップを容易に公開できるようサポートするものです。

## 利用方法

1. [shikuchoson-hazardmap-template](https://github.com/sankichi92/shikuchoson-hazardmap-template) リポジトリを使用してGitHubリポジトリを作成
2. `hazardmap-config.jsonc`ファイルを編集して対象の市区町村を設定
3. GitHubの設定からGitHub Pagesを有効化し、Webページを公開

詳細は[README](https://github.com/sankichi92/shikuchoson-hazardmap-template#使い方)を参照してください。