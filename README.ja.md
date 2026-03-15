# 越前市ハザードマップ

- [越前市ハザードマップ](https://code4fukui.github.io/echizencity-hazardmap/)
- [越前市オープンデータ](https://www.city.echizen.lg.jp/office/010/021/open-data-echizen.html)から、広域避難所、AED、医療機関を使用

## 市区町村ハザードマップテンプレート

市区町村の Web ハザードマップを作成するためのテンプレート「[市区町村ハザードマップテンプレート](https://github.com/sankichi92/shikuchoson-hazardmap-template)」を使用しています

[Tokyo OSS Party!!](https://tokyo-oss-party.com/) 2021 の成果物です。\
発表資料は https://speakerdeck.com/sankichi92/shikuchoson-hazardmap-template

## 利用例

- [八王子市](https://sankichi.net/hachioji-hazardmap/) ([sankichi92/hachioji-hazardmap](https://github.com/sankichi92/hachioji-hazardmap))

## 背景と課題

日本のハザードマップは、国土交通省の管理する[ハザードマップポータルサイト](https://disaportal.gsi.go.jp/)にまとめられており、そこでは以下の2つのサービスが提供されています。

- 重ねるハザードマップ: 災害リスク情報や防災に役立つ情報を、全国どこでも重ねて閲覧できるWeb地図サイト
- わがまちハザードマップ: 市町村が作成したハザードマップを見つけやすくまとめたリンク集

「重ねるハザードマップ」は Web 地図として多機能で非常によく作りこまれていますが、その[使い方](https://disaportal.gsi.go.jp/hazardmap/pamphlet/pamphlet.html)でも

> 詳細を確認する場合は市町村が作成したハザードマップをご覧ください。

とあるとおり、あくまで国の作成した地図であり、市区町村ごとの詳細は確認できません。

ハザードマップに求められるのは、多くの場合、国全体の広く浅い情報ではなく、自身の住む場所ピンポイントの狭く深い情報です。
そうした情報を確認するには、「わがまちハザードマップ」から市区町村のハザードマップを確認する必要があります。

しかし、市区町村の作成するハザードマップの多くが紙での配布を前提としており、重ねるハザードマップとちがって Web に最適化されていません。
そしておそらく、独自の Web ハザードマップを開発・運用できるほど、予算やリソースに余裕のある市区町村は少ないでしょう。

この課題に対し、本プロジェクトは、市区町村の単位で Web ハザードマップを容易に作成・カスタマイズできるテンプレートを提供します。