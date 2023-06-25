---
title: "分割代入について"
emoji: "📂"
type: "tech"
topics: ["rabee", "frontend"]
publication_name: "rabee"
published: false
---

# 始めに
JavaScriptではオブジェクトの分割代入を利用すると、オブジェクトから特定のプロパティを取り出し、それらを個別の変数に代入することができます。
オブジェクトの場合、分割代入はオブジェクトのプロパティ名に基づいて行われます。
# 分割代入の例
## オブジェクトの分割代入
```js
{
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'lion',
      age: 10,
    },
  }
};
```
分割代入によって受け取ると
```js
let { contents } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'lion',
      age: 10,
    },
  }
};

console.log(contents);
// =>　{
//   "users": {
//     "name": "takashi",
//     "age": 20
//   },
//   "animals": {
//     "name": "lion",
//     "age": 10
//   },
// }
```
このようになります。

## ネストしたオブジェクトの分割代入
```js
let { contents: { users } } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'lion',
      age: 10,
    },
  }
};
console.log(users);
// =>　{
//   "name": "takashi",
//   "age": 20
// }
```
このように複数受け取ることも可能です。

```js
let { contents: { users, animals } } = {
  contents: {
    users: {
      name: 'takashi',
      age: 20,
    },
    animals: {
      name: 'lion',
      age: 10,
    },
  }
};
console.log(users);
// =>　{
//   "name": "takashi",
//   "age": 20
// }
console.log(animals);
// => {
//   name: 'lion',
//   age: 10,
// }
```
## はデフォルト値を指定した分割代入
例えばこのような場合があります。
```js
let [
  { collection }, 
  { project }
] = [
  { collection: { id: 'abcd', name: 'hoge' } }, 
  { project: { id: '12345', name: 'fuga' } }
];
```
上記では、collectionとprojectの変数に分割代入されます。

ですが、以下のような場合エラーが発生します。
```js
let [
  { collection }, 
  { project }
] = [
  { collection: { id: 'abcd', name: 'hoge' } }
];
```
"Cannot read properties of undefined (reading 'project')"となります。
これを回避するためには、projectにデフォルト値を設定します。
```js
let [
  { collection }, 
  { project }  = {}
] = [
  { collection: { id: 'abcd', name: 'hoge' } }
];
```
こうすることで、projectがない場合でもエラーを回避することができます。

# 最後に
このように、分割代入をうまく活用することで、より効率的で簡潔なコードを書くことができます。ただし、代入元のオブジェクトや配列の構造が予測不能な場合や、デフォルト値を適切に設定しない場合は、エラーが発生する可能性があるため注意が必要です。