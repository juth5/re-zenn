---
title: "CSSで縁(ボーダー)がグラデーションの角丸ボタンを作る方法"
emoji: "🖋"
type: "tech"
topics: ["HTML", "CSS", "rabee"]
publication_name: "rabee"
published: false
---

# 初めに
cssを用いて、縁(ボーダー)がグラデーションの角丸ボタンを作りたい時はありませんか？これを作るには、少し工夫が必要みたいです。
![](https://storage.googleapis.com/zenn-user-upload/33ee23676595-20230415.png)
# 実装例
私は、縁がグラデーションのボタンを作り、その角を丸めれば実現できると考え以下のようなボタンを作成しました。
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
角を丸めるには.buttonクラスに以下のようにborder-radiusを指定すれば実現できると思いました。
```
.button {
  width: 100px;
  height: 30px;
  border: 1px solid;
  border-image: linear-gradient(to right, #00ffd5 0%, #0f3dd7 100%);
  border-image-slice: 1; 
  text-align: center;
  <!-- この箇所を追記 -->
  border-radius: 9999px;
}
```
ですが、これでは丸くなりませんでした。

![](https://storage.googleapis.com/zenn-user-upload/32c34838cc67-20230415.png)


調べた結果、グラデーションが一面にかかった要素にグラデーションがかかっていない要素を被せることで実現できました。

HTML
```
<div class='outer-button'>
  <div class='inner-button'>button</div>
</div>
```
CSS
```
.outer-button {
  width: 100px;
  height: 30px;
  background:  linear-gradient(to right, #00ffd5 0%, #0f3dd7 100%);
  border-radius: 9999px;
  // paddingの値がborderの太さ
  padding: 2px;
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

その上に、グラデーションがかかっていない要素(.inner-buttonクラスが当たっている要素)を被せるとで実現ができました。

![](https://storage.googleapis.com/zenn-user-upload/33ee23676595-20230415.png)

縁の太さは、.outer-buttonクラスが当たっている要素にpaddingを付与することで調整ができます。

# 最後に
ボーダーをグラデーションにしたい時は、border-imageプロパティを使えば実現できますが、角丸にするためのborder-radiusプロパティは使えないみたいです。
今回の方法は、グラデーションがかかった背景の上にもう一つ要素を乗せることでグラデーションのボーダーが引かれているように見せています。
別の方法があれば教えていただきたいです。