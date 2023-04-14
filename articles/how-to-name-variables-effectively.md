---
title: "「変数名で認識のズレをなくし、半角スペースが消されないようにしよう」"
emoji: "🖋"
type: "tech"
topics: ["HTML", "JavaScript", "rabee"]
publication_name: "rabee"
published: true
---

# 初めに

文字列処理などで、意図的に半角スペースを入れたいことってありませんか？そのような場合の注意点を記事にまとめてみました。

# 半角スペースを入れたい場合の実装例
以下のようなデータがあります。
```js
let tags = ["HTML", "CSS", "JavaScript"];
```

そのデータを、以下のような文字列に整形して表示したいと考えます。
``` js
"#HTML #CSS #JavaScript"
```

joinメソッドを使って、以下のように書くと`#`が文字列の先頭につき文字列と文字列の間には半角スペースが差し込まれます。
```js
let tagNames = `#${tags.join(' #')}`;
console.log(tagNames);
// =>　"#HTML #CSS #JavaScript"
```

しかしこのような実装をしてしまうと、チーム開発の際にjoinメソッドの引数の`#`の前に入れている半角スペースが不要なものと思われ、消されてしまう恐れがあります。
ですが、半角スペースも変数に入れることで勘違いにより消されてしまうことを防ぐことができます。
```js
let SEPARATOR = ' ';
let tagNames = `#${tags.join(SEPARATOR + '#')}`;
console.log(tagNames);
// =>　"#HTML #CSS #JavaScript"
```

この時、変数名を`SEPARATOR`（区切り文字）とするとどのような目的で半角スペースを入れているのかわかりやすくなり、コードの可読性が高まります。

# 補足
ここからは補足で、先輩社員から「根本的にロジックが悪いため、余計に勘違いを引き起こし半角スペースを消されてしまう恐れがある」という指摘をいただきました。
そのため、以下のロジックで修正を行いました。

1. mapを使って、`#`を文字列の頭につけます。
2. joinを使って、半角スペースで結合します。

```js
let tags = ["HTML", "CSS", "JavaScript"];

tags = tags.map(tag => '#' + tag);
console.log(tags);
// => ["#HTML", "#CSS", "#JavaScript"];
tags = tags.join(' ');
console.log(tags);
// => #HTML #CSS #JavaScript;
```

コードがすっきりしました。また、半角スペースを消されるという問題を考慮する必要もなくなりました。

# 最後に
チーム開発では、可読性がとても大切になります。参考にしていただけると幸いです。