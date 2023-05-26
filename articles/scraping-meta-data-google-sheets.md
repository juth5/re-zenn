---
title: "GoogleスプレッドシートでWebサイトのメタ情報を抽出する方法"
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

# XPathとは？

XPath（XML Path Language）は、XML文書内の要素や属性を選択するための言語です。XPathは、階層的なパス表現を用いて、XML文書内の位置を表現します。これにより、特定の要素や属性を指定して抽出したり、特定のパターンに一致するノードを検索したりすることができます。
XPathの基本的な構文は、ファイルシステムのディレクトリ構造をナビゲートする方法に似ています。
一部ですが、指定方法の例を紹介します。
## タグ（要素）で指定する場合

例えば以下のようなHTMLのドキュメントがあります。
```js
<div>
  <article>
    <h1>パン屋さん</h1>
    <p id='description'>カレーパンが美味しいです。</p>
  </article>
</div>
```
このHTMLから『パン屋さん』を取得したい場合は以下のような、絶対XPathという書き方と
```
/html/body/div/article/h1
```
『//』を用いて、途中までのパスを省略する、短いXPathと呼ばれる書き方があります。
```
//article/h1
```
## 属性で指定する場合
XPathでは属性を『@』関数で表します。
例えば、『カレーパンが美味しいです。』を取得したい場合、次のように書きます。
```
//p[@id=description]
```
抽象化すると以下のようになります。
```
//タグ名[@属性名=”属性値”]
```
また、同じ属性を持つすべての要素を取得する場合は、
```
//*[@属性名=”属性値”]
```
のように書きます。

その他、Xpathの書き方よく使う関数については以下の記事をお読みください。
https://www.octoparse.jp/blog/xpath-introduction
# メタ情報の抽出方法
例としてトヨタ自動車のHPのメタ情報を抽出してみたいと思います。
Webサイトのメタ情報のタイトルを抽出する際は以下のように関数を入力します。
```
=IMPORTXML(URL, "//title")
```
![](https://storage.googleapis.com/zenn-user-upload/4ad83e247977-20230513.png)
descriptionの場合は、以下のように関数を入力します。
```
=IMPORTXML(URL, "//meta[@name='description']/@content")
```
![](https://storage.googleapis.com/zenn-user-upload/db58103fe889-20230513.png)

このように、URLさえ指定すればWebサイトのメタ情報を一括で抽出することができます。
# その他のメタ情報について
その他、主要なメタ情報取得の関数の記載方法をまとめています。
| データ | 入力例   |
|---------|--------|
| meta og:image    | =IMPORTXML(URL,”//meta[@property=’og:image’]/@content”) |
| meta keywords  | =IMPORTXML(URL,”//meta[@name=’keywords’]/@content”)   |
| canonical URL| =IMPORTXML(URL,”//link[@rel=’canonical’]/@href”) |

# 最後に
この記事では、Googleスプレッドシートを活用してWebサイトのメタ情報を抽出する方法について詳しく解説しました。カスタム関数やスクリプトを使用することで、短時間で多くのWebページからメタ情報を取得し、スプレッドシート上で編集・整理することができます。この手法は、SEO分析や競合サイトの調査、コンテンツの概要把握に役立ちます。また、クラウドベースのGoogleスプレッドシートを使用することで、データの共有やコラボレーションが容易になります。