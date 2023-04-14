---
title: "CSSで角丸で縁がグラデーションのボタンを作る方法"
emoji: "🖋"
type: "tech"
topics: ["HTML", "rabee"]
publication_name: "rabee"
published: false
---

# 初めに
cssで、角丸で縁(border)がグラデーションのボタンを作りたい時はありませんか？これを作るには、少し工夫が必要みたいです。
# 実装例
まずは、角丸ではない縁がグラデーションのボタンを作成してみます。
1. HTMLでボタンを作成
HTMLでボタンを作成します。
```
<button class="button">Button</button>
```
2. CSSでスタイルを設定

```
.button {
  width: 100px;
  height: 30px;
  border: 1px solid;
  border-image: linear-gradient(to right, #00ffd5 0%, #0f3dd7 100%);
  border-image-slice: 1; 
  text-align: center;
}
```
すると以下のようなボタンができます。

これを角丸にしようと思うと、.buttonクラスに以下のようにborder-radiusを指定すれば実現すると考えると思います。
※角を丸くするために、9999pxを指定。
```
.button {
  border-radius: 9999px;
}
```
ですが、これでは丸くなりません。


実現の方法は、グラデーションが一面にかかった要素にグラデーションがかかっていない要素を被せることで実現できます。

HTML
```
<div class='outer-button'>
  <div class='inner-button'>button</div>
</div>
```

CSS
```js
.outer-button {
  width: 100px;
  height: 30px;
  // paddingの値がborderの太さ
  padding: 1px;
  background:  linear-gradient(to right, #00ffd5 0%, #0f3dd7 100%);
  border-radius: 9999px;
}

.inner-button {
  width: 100px;
  height: 30px;
  background: white;
  border-radius: 9999px;
  text-align: center;
}
```

# 最後に
