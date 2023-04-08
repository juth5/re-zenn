---
title: "空白を入れる時の対応"
emoji: "🖋"
type: "tech"
topics: ["HTML", "JavaScript"]
published: false
---

# コード中にあえて半角スペースを入れたい時ってありませんか？
半角スペースも変数に代入することで、予期せぬバグを防ぐことができます。
以下は例です。
このようなデータがあります。

```js
let tags = ["HTML", "CSS", "JavaScript"];
```

tagsというデータを、以下のような文字列に整形して表示したいと考えます。
``` js
"#HTML #CSS #JavaScript"
```

tagsに対してjoinメソッドを使って整形します。
タグとタグの間に半角スペースを入れるためにjoinメソッドの中で`#`の前にあえて、半角スペースを入れています。
```js
let tagNames = `#${tags.join(' #')}`;
console.log(tagNames);
"#HTML #CSS #JavaScript"
```

このような実装をしてしまうと、チーム開発の際にその意図を汲み取れずに余計な半角スペースが入っていると判断されて消されてしまう恐れがあります。
半角スペースも変数名に入れることで解決することができます。
```js
let SEPARATOR = ' ';
let tagNames = `#${tags.join(SEPARATOR + '#')}`;
console.log(tagNames);
"#HTML #CSS #JavaScript"
```

さらに、`SEPARATOR`（区切り文字）という変数名も何のための半角スペースなのか意味がわかる名前にしましょう！