---
title: "デベロッパーツールでUser-Agentを偽装する方法"
emoji: "🤳"
type: "tech"
topics: ["rabee"]
publication_name: "rabee"
published: false
---

# 初めに
最近、SEO対策の一環として、User-Agentがbotの場合に特定の処理を行わないようにする実装を行いました。この記事では、Google Chromeのデベロッパーツールを使ってUser-Agentを偽装する方法を紹介します。
# User-Agentとは
ユーザーエージェント（User-Agent）とは、インターネットを閲覧しているユーザーの、デバイス・OS・ブラウザなどの情報のことです。
# ChromeでUser-Agentを変更する方法

1. デベロッパーツールを起動します

2. More ToolsからNetwork conditionsを開く
デベロッパーツールを起動して、右隅の「･･･」アイコンをクリックすると以下のようなメニューが開くので、「その他のツール」から「ネットワーク状態」をクリックしてください。
![](https://storage.googleapis.com/zenn-user-upload/a533256b393f-20230421.png)

3. select automaticallyのチェックを外す
![](https://storage.googleapis.com/zenn-user-upload/6c6cc643bb94-20230421.png)
パネルの箇所に、ネットワーク状態のタブが表示されことを確認し、ブラウザのデフォルトを仕様のチェックを外してください。
4. UserAgentを変える
User-Agentを選択できるので必要なものに変更してください。
![](https://storage.googleapis.com/zenn-user-upload/53bd77ed3e44-20230421.png)
5. 変更後、デベロッパーツールを開いた状態でリロードすればUserAgentを偽装することができます。

# 最後に
