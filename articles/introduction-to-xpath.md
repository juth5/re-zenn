---
title: "XPath入門"
emoji: "📂"
type: "tech"
topics: ["rabee", "frontend"]
publication_name: "rabee"
published: false
---


# XPathとは？
XPath（XML Path Language）は、XML文書内の要素や属性を選択するための言語です。XPathは、階層的なパス表現を用いて、XML文書内の位置を表現します。これにより、特定の要素や属性を指定して抽出したり、特定のパターンに一致するノードを検索したりすることができます。
XPathの基本的な構文は、ファイルシステムのディレクトリ構造をナビゲートする方法に似ています。
一部ですが、指定方法の例を紹介します。

## タグ（要素）で指定する場合
```js
<div>
  <article>
    <h1>パン屋さん</h1>
    <p>カレーパンが美味しいです。</p>
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
```js
<div>
  <article>
    <h1>パン屋さん</h1>
    <p id='description'>カレーパンが美味しいです。</p>
  </article>
</div>
```
例えば、『カレーパンが美味しいです。』を取得したい場合、次のように書きます。
```
//p[@id=description]
```
抽象化すると以下のようになります。
```
//タグ名[@属性名="属性値"]
```
また、同じ属性を持つすべての要素を取得する場合は、
```
//*[@属性名="属性値"]
```
のように書きます。


## クラスで指定する場合
```
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
