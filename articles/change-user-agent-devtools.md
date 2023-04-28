---
title: "デベロッパーツールでUser-AgentをGooglebotに偽装する方法"
emoji: "🤳"
type: "tech"
topics: ["rabee", "googlechrome", "frontend"]
publication_name: "rabee"
published: false
---

# 初めに
SEO対策の一環としてUser-AgentがGooglebot(bot)の場合に特定の処理を行わないようにする実装を行いました。その際の動作検証で、Google ChromeのデベロッパーツールでUser-AgentをGooglebot(bot)に偽装する方法を知ったのでその方法を紹介します。
# User-Agentとは
ユーザーエージェント（User-Agent）とは、インターネットを閲覧しているユーザーの、デバイス・OS・ブラウザなどの情報のことです。一般的なインターネットブラウザを使い、HTTPに基づきサイトなどにアクセスした際には、ユーザーエージェントに関する各種情報が、相手側に通知される仕組みとなっているためアクセス解析に使われたりもします。
# ChromeでUser-Agentを変更する方法

1. デベロッパーツールを起動

2. ネットワーク状態を開く
デベロッパーツールを起動して、右隅の「･･･」アイコンをクリックすると以下のようなメニューが開くので、「その他のツール」から「ネットワーク状態」をクリックしてください。
![](https://storage.googleapis.com/zenn-user-upload/d1886c8905ba-20230421.png)
![](https://storage.googleapis.com/zenn-user-upload/217946591a9d-20230428.png)
3. ブラウザのデフォルトを使用のチェックを外す
ネットワーク状態のタブを選択して、ブラウザのデフォルトを使用のチェックを外してください。
![](https://storage.googleapis.com/zenn-user-upload/ea6d7d78b197-20230421.png)

4. UserAgentを変える
ブラウザのデフォルトを使用のチェックを外すと、User-Agentを選択できるので必要なものに変更してください。
![](https://storage.googleapis.com/zenn-user-upload/53bd77ed3e44-20230421.png)
5. 変更後、デベロッパーツールを開いた状態でリロードすればUserAgentを偽装することができます。

# 最後に
Google Chromeのデベロッパーツールを使用してUser-Agentを偽装する方法を紹介しました。この方法を利用することで、実装したSEO対策がGooglebot(bot)に適切に機能しているかどうかを確認することができます。参考にしていただけると幸いです。