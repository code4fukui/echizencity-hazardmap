# echizencity-hazardmap

このリポジトリには、福井県越前市の災害リスクと安全情報を可視化するWeb版ハザードマップ「[Echizen City Hazard Map](https://code4fukui.github.io/echizencity-hazardmap/)」のソースコードが含まれています。

避難所、AED設置場所、医療機関など、[越前市オープンデータ](https://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html)のオープンデータを活用しています。

![Echizen City Hazard Map Screenshot](https://raw.githubusercontent.com/sankichi92/shikuchoson-hazardmap-template/main/docs/screenshot.png)

## テンプレートについて

このプロジェクトは、市区町村が独自のWeb版ハザードマップを簡単に作成・公開できるように設計された、**[市区町村ハザードマップテンプレート](https://github.com/sankichi92/shikuchoson-hazardmap-template)** の実装例です。

このテンプレートは、[Tokyo OSS Party!! 2021](https://tokyo-oss-party.com/) の成果物として作成されました。
- **プレゼン資料:** [speakerdeck.com/sankichi92/shikuchoson-hazardmap-template](https://speakerdeck.com/sankichi92/shikuchoson-hazardmap-template)
- **テンプレート使用例:** [八王子市ハザードマップ](https://sankichi.net/hachioji-hazardmap/) ([GitHub Repo](https://github.com/sankichi92/hachioji-hazardmap))

## 背景

日本のハザードマップは、国土交通省が管理する[ハザードマップポータルサイト](https://disaportal.gsi.go.jp/)に集約されています。このポータルの「重ねるハザードマップ」は全国を網羅する強力なツールですが、住民が必要とする詳細な地域情報が不足しています。ポータルサイト自体でも「詳細を確認する場合は市町村が作成したハザードマップをご覧ください」と案内されています。

しかし、多くの市区町村のハザードマップは紙での配布を前提としており、Webに最適化されていません。また、独自のインタラクティブなWeb地図を開発・運用する予算やリソースが不足している市区町村も少なくありません。このテンプレートは、標準化されたオープンソースのフレームワークを活用し、Web版ハザードマップの作成とカスタマイズを容易にすることで、この課題に対する解決策を提供します。

## 独自のハザードマップの作成方法

以下の手順で、任意の市区町村のハザードマップを作成できます。

チュートリアル動画を見る: [https://youtu.be/oc1CfaVSlno](https://youtu.be/oc1CfaVSlno)

#### 1. テンプレートからリポジトリを作成する

1. [テンプレートのリポジトリ](https://github.com/sankichi92/shikuchoson-hazardmap-template)にアクセスします。
2. **"Use this template"** ボタンをクリックします。
3. リポジトリ名（例: `mycity-hazardmap`）を入力し、**"Create repository from template"** をクリックします。

（参考 GitHub Docs: [Creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)）

#### 2. 市区町村向けの設定を行う

1. 新しいリポジトリで `hazardmap-config.jsonc` ファイルを開きます。
2. 鉛筆アイコン（✏️）をクリックしてファイルを編集します。
3. `prefecture`（都道府県）と `city`（市区町村）の値を対象の自治体に変更します。
4. `tiles` 配列から不要なハザードレイヤを削除します（例: 内陸部の市区町村の場合は「高潮浸水想定区域」など）。
5. **"Commit changes"** をクリックします。

（参考 GitHub Docs: [Editing files in your repository](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files#editing-files-in-your-repository)）

#### 3. GitHub Pagesで公開する

1. リポジトリの **Settings** タブを開き、サイドバーから **Pages** を選択します。
2. **Source** の設定で `gh-pages` ブランチを選択します。
3. **"Save"** をクリックします。
4. 数分後、ページ上に表示されたURLでハザードマップが公開されます。ビルドとデプロイのプロセスは GitHub Actions によって自動的に処理されます。

（参考 GitHub Docs: [Configuring a publishing source for your GitHub Pages site](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)）

## カスタマイズ

#### カスタムデータレイヤの追加（CSV）

1. リポジトリ内の `csv` ディレクトリに移動します。
2. **"Add file"** > **"Upload files"** をクリックして、独自のCSVデータを追加します。
3. CSVファイルには `name`、`lat`（緯度）、`lon`（経度）の列が含まれている必要があります。その他の列を追加した場合、地図上のアイコンをクリックした際のポップアップに表示されます。
4. ファイル名のプレフィックス（例: `01-`）によって、レイヤコントロールでの表示順が決定されます。

（参考 GitHub Docs: [Adding a file to a repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)）

#### カスタム凡例画像の追加

1. `images` ディレクトリに移動します。
2. 凡例画像（PNG、JPGなど）をアップロードします。アップロードした画像は、地図の左下に自動的に表示されます。

## 開発

このプロジェクトは [Create React App](https://github.com/facebook/create-react-app) を使用して構築されています。ローカルでプロジェクトを実行するには以下の手順に従います。

1. リポジトリをクローンします。
2. 依存関係をインストールします: `npm install`
3. プレビルドスクリプトを実行し、設定とデータを処理します: `npm run prebuild`
4. 開発サーバーを起動します: `npm start`

### 利用可能なスクリプト

- **`npm start`**: アプリを開発モードで実行します。[http://localhost:3000](http://localhost:3000) で確認できます。
- **`npm run build`**: 本番環境用のアプリを `build` ディレクトリにビルドします。
- **`npm run prebuild`**: `hazardmap-config.jsonc`、`csv`、`images` の各ファイルをアプリケーションで利用可能な形式に処理します。これらのファイルを変更した場合は、`npm start` の前にこのコマンドを実行する必要があります。
- **`npm run format`**: [Prettier](https://prettier.io/) を使用してコードをフォーマットします。

## ライセンス

このプロジェクトは [MIT License](LICENSE) のもとで公開されています。
