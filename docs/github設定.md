# コンテナ内githubの認証設定

[Remote Development](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)ではホストPCのSSHエージェントに登録された認証情報を自動でコンテナに複製します。
これによって、github認証情報をコンテナの起動ごとに入力する必要がなくなります。

1. githubアカウントへ公開鍵の登録
2. SSHエージェントのインストールと秘密鍵の登録

## 参考

* [Visual StudioCodeリモート開発を使用したコンテナー内での開発](https://code.visualstudio.com/docs/remote/containers#_sharing-git-credentials-with-your-container)
* [Connecting to GitHub with SSH - GitHub Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
