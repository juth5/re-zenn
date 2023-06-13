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
# 例
データ取得の際に、以下のような形のオブジェクトが返ってくるとします。
```js
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
分割代入によって受け取ると
```js
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
このようになります。


さらに、usersというキーのバリューを分割代入によって受け取るには以下のように書きます。
```js
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

```js
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
分割代入を行う際のデフォルト値について
例えばこのような場合があります。
```js
let [{ collection }, { project }] = [{collection: {id: 'abcd', name: 'hoge'}}, {project: { id: '12345', name: 'fuga' }}];
```
上記では、collectionとprojectの変数に分割代入されます。

ですが、以下のような場合エラーが発生します。
```js
let [{ collection }, { project }] = [{collection: {id: 'abcd', name: 'hoge'}}];
```
"Cannot read properties of undefined (reading 'project')"となります。
これを回避するためには、projectにデフォルト値を設定します。
```js
let [{ collection }, { project }={}] = [{collection: {id: 'abcd', name: 'hoge'}}];
```
こうすることで、projectがない場合でもエラーを回避することができます。


https://runstant.com/fukagawa/projects/6ace5bf9
# 最後に
