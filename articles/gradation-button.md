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
まずは、角丸ではないボタンで縁がグラデーションのボタンを作成してみます。
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

![画像の説明](images/%E3%82%B9%E3%82%AF%E3%83%AA%E3%83%BC%E3%83%B3%E3%82%B7%E3%83%A7%E3%83%83%E3%83%88%202023-04-15%201.14.35.png)



# 最後に
