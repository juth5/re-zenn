---
title: "CSSでボーダーがグラデーションの角丸ボタンを作る方法"
emoji: "🟡"
type: "tech"
topics: ["HTML", "CSS", "rabee"]
publication_name: "rabee"
published: true
---

# 初めに
CSSを用いて、ボーダーがグラデーションの角丸ボタンを作りたい時はありませんか？これを作るには、少し工夫が必要みたいです。
![](https://storage.googleapis.com/zenn-user-upload/b9d730b73da9-20230418.png)
# 上手くいかなかった実装例
私は、まずボーダーがグラデーションの四角のボタンを作り、その角を丸めれば実現できると考え以下のようなボタンを作成しました。
![](https://storage.googleapis.com/zenn-user-upload/f5be9c9d74be-20230418.png)
HTMLでボタンを作成
```
<button class="button">button</button>
```
CSSでスタイルを設定

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
角を丸めるにはbuttonクラスに以下のようにborder-radiusプロパティを付与すれば実現できると考えました。
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

![](https://storage.googleapis.com/zenn-user-upload/f5be9c9d74be-20230418.png)

別の方法を調べた結果、グラデーションが一面にかかった要素にグラデーションがかかっていない要素を重ねることで実現できました。

# 上手くいった実装例

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
グラデーションが一面にかかった要素(outer-buttonクラスが当たっている要素)に、
![](https://storage.googleapis.com/zenn-user-upload/a92920556528-20230418.png)

グラデーションがかかっていない要素(inner-buttonクラスが当たっている要素)を重ねることで、以下のようなボタンが実現できました。

![](https://storage.googleapis.com/zenn-user-upload/b9d730b73da9-20230418.png)
ボーダーの太さは、outer-buttonクラスが当たっている要素にpaddingを付与することで調整ができます。

https://runstant.com/fukagawa/projects/20949fc8

# 最後に
ボーダーをグラデーションにしたい時は、border-imageプロパティを使えば実現できますが、角丸にするためのborder-radiusプロパティは使えないみたいです。
今回の方法は、グラデーションがかかった背景の上にもう一つ要素を重ねることでグラデーションのボーダーが引かれているように見せています。
別の方法があれば教えていただきたいです。
