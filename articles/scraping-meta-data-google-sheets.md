---
title: "GoogleスプレッドシートでWebサイトのmeta情報を抽出する方法"
emoji: "📂"
type: "tech"
topics: ["rabee", "googlesheets", "frontend"]
publication_name: "rabee"
published: false
---

# 始めに
Webサイトのメタ情報は、検索エンジン最適化（SEO）やコンテンツの概要把握に非常に重要な役割を果たしています。メタ情報を抽出することで、競合サイトのSEO戦略や、特定のキーワードをターゲットにしたコンテンツの分析が可能になります。しかし、多くのWebページからメタ情報を効率的に収集・整理するには、適切なツールや技術が必要です。この記事では、Googleスプレッドシートを使用してWebサイトのメタ情報を抽出する方法を解説します。
# IMPORTXML関数について
IMPORTXML関数は、XML、HTML、CSV、TSV、RSS フィード、Atom XML フィードなど、さまざまな種類の構造化データからデータをインポートできるGoogleスプレッドシートの関数です。
構文は以下のようになります。
```
IMPORTXML(URL, xpath_query)
```
# メタ情報の抽出方法
例としてトヨタ自動車のHPのメタ情報を抽出してみたいと思います。
Webサイトのメタ情報のタイトルを抽出する際は以下のように関数を入力します。
```
=IMPORTXML(URL, "//title")
```
![](https://storage.googleapis.com/zenn-user-upload/02bfbc0cf9c4-20230512.png)
descriptionの場合は、以下のように関数を入力します。
```
=IMPORTXML(URL, "//meta[@name='description']/@content")
```
![](https://storage.googleapis.com/zenn-user-upload/ef2650451e28-20230512.png)

# その他

| カテゴリ | 名称   |
|---------|--------|
| 果物    | りんご |
| おかし  | あめ   |
| ジュース| コーラ |

# 最後に
この記事では、Googleスプレッドシートを活用してWebサイトのメタ情報を抽出する方法について詳しく解説しました。カスタム関数やスクリプトを使用することで、短時間で多くのWebページからメタ情報を取得し、スプレッドシート上で編集・整理することができます。この手法は、SEO分析や競合サイトの調査、コンテンツの概要把握に役立ちます。また、クラウドベースのGoogleスプレッドシートを使用することで、データの共有やコラボレーションが容易になります。