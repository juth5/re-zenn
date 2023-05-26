---
title: "分割代入について"
emoji: "📂"
type: "tech"
topics: ["rabee", "frontend"]
publication_name: "rabee"
published: false
---

# 始めに
# 例
データ取得の際に、以下のような形のオブジェクトが返ってくるとします。
```
{
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'rion',
      age: 10,
    },
  }
};
```
分割代入によって
```
let { contents } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'rion',
      age: 10,
    },
  }
};

console.log(contents);
// =>　{
  "users": {
    "name": "takashi",
    "age": 20
  },
  "animals": {
    "name": "rion",
    "age": 10
  },
```

分割代入によって
```
let { contents: { users } } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'rion',
      age: 10,
    },
  }
};
console.log(users);
// =>　{
  "name": "takashi",
  "age": 20
}
```
また、このように複数受け取ることも可能です。
```
let { contents: { users, animals } } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'rion',
      age: 10,
    },
  }
};
console.log(users);
// =>　{
  "name": "takashi",
  "age": 20
}
console.log(animals);
// => {
  name: 'rion',
  age: 10,
}

```
https://runstant.com/fukagawa/projects/6ace5bf9
# メタ情報の抽出方法

# その他のメタ情報について
# 最後に
