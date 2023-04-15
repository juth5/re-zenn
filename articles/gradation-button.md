---
title: "CSSで角丸で縁がグラデーションのボタンを作る方法"
emoji: "🖋"
type: "tech"
topics: ["HTML", "rabee"]
publication_name: "rabee"
published: false
---

# 初めに
cssを用いて、角丸で縁(border)がグラデーションのボタンを作りたい時はありませんか？これを作るには、少し工夫が必要みたいです。
![](https://storage.googleapis.com/zenn-user-upload/33ee23676595-20230415.png)
# 実装例
まずは、角丸ではない縁がグラデーションのボタンを作成してみます。
![](https://storage.googleapis.com/zenn-user-upload/32c34838cc67-20230415.png)

1. HTMLでボタンを作成
```
<button class="button">button</button>
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

これを角丸にしようと思うと、.buttonクラスに以下のようにborder-radiusを指定すれば実現できると思いませんか？
※角を丸くするために、9999pxを指定。
```
.button {
  width: 100px;
  height: 30px;
  border: 1px solid;
  border-image: linear-gradient(to right, #00ffd5 0%, #0f3dd7 100%);
  border-image-slice: 1; 
  text-align: center;
  <!-- この箇所を追記して角を丸めようと考えます -->
  border-radius: 9999px;
}
```
ですが、これでは丸くなりません。

![](https://storage.googleapis.com/zenn-user-upload/32c34838cc67-20230415.png)


実現の方法として、グラデーションが一面にかかった要素にグラデーションがかかっていない要素を被せることで実現できます。

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
  padding: 2px;
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
グラデーションが一面にかかった要素(.outer-buttonクラスが当たっている要素)
![](https://storage.googleapis.com/zenn-user-upload/557fe15396af-20230415.png)

その上に、グラデーションがかかっていない要素を被せると実現ができます。(.inner-buttonクラスが当たっている要素)

![](https://storage.googleapis.com/zenn-user-upload/33ee23676595-20230415.png)

縁の太さは、.outer-buttonクラスが当たっている要素にpaddingを付与することで調整ができます。

# 最後に
