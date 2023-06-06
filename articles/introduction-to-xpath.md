---
title: "XPathについて"
emoji: "📄"
type: "tech"
topics: ["rabee", "frontend"]
publication_name: "rabee"
published: false
---


# XPathとは？
XPath（XML Path Language）とは、XML文書内の要素や属性を選択するための言語です。階層的なパス表現を用いてXML文書内の位置を表現し、特定の要素や属性を指定して抽出したり、特定のパターンに一致するノードを検索したりします。XPathの基本的な構文は、ファイルシステムのディレクトリ構造をナビゲートする方法に似ています。この記事では、その基本的な使い方をいくつか紹介します。
## タグ（要素）で指定する場合
タグ（要素）を指定して情報を抽出する方法を見ていきましょう。例えば、以下のようなHTML文書があります。
```js
<div>
  <article>
    <h1>パン屋さん</h1>
    <p>カレーパンが美味しいです。</p>
  </article>
</div>
```
このHTMLから『パン屋さん』を取得するためには、絶対XPathの書き方や、"//"を用いて途中までのパスを省略する短いXPathの書き方があります。
絶対XPathは以下のようになります。
```
/html/body/div/article/h1
```
短いXPathは以下のようになります。
```
//article/h1
```
## 属性で指定する場合
次に属性を指定して情報を抽出する方法を見ていきましょう。XPathでは属性を"@"で表現します。例えば、以下のようなHTML文書があります。
```js
<div>
  <article>
    <h1>パン屋さん</h1>
    <p id='description'>カレーパンが美味しいです。</p>
  </article>
</div>
```
"カレーパンが美味しいです。"というテキストを持つp要素を取得するには、以下のように書きます。
```
//p[@id=description]
```
一般化すると、この形になります。
```
//タグ名[@属性名="属性値"]
```

そして、特定の属性値を持つすべての要素を取得するには、以下のように書きます。
```
//*[@属性名="属性値"]
```
のように書きます。


## クラスで指定する場合
```
例えば、以下のようなHTML文書があります。
<div>
  <article class='featured'>
    <h1>コーヒーショップ</h1>
    <p class='description'>自家焙煎のコーヒー豆が自慢です。</p>
  </article>
</div>
```
クラス名が 'featured' のarticle要素を取得したい場合、次のようなXPathを使用します。

```
//article[@class='featured']
```
### ネストされた要素で指定する場合
XPathはネストされた要素の抽出にも非常に便利です。以下のようなHTML文書があります。
```
<div>
  <ul id='menu'>
    <li class='item'>ホットコーヒー</li>
    <li class='item'>アイスコーヒー</li>
    <li class='item'>カフェラテ</li>
  </ul>
</div>
```
ここで、idが 'menu' のul要素の下にあるすべてのli要素を取得したい場合、次のようなXPathを使用します。
```
//ul[@id='menu']/li
```
また、クラス名が 'item' のすべてのli要素を取得したい場合、次のようにします。
```
//li[@class='item']
```


その他、Xpathの書き方よく使う関数については以下の記事をお読みください。
https://www.octoparse.jp/blog/xpath-introduction
# 最後に
XPathを理解し使いこなすことで、XMLデータの抽出がより効率的になり、作業がスムーズに進行します。ぜひ活用してみてください。