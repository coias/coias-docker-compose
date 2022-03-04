# coias-docker-compose

coiasの開発環境およびWebアプリを構築します。docker-composeを使用することで、簡単に構築できます。  
docker,docker-composeを使用し、フロントエンドアプリ、バックエンドアプリ、API、webサーバーなどを自動実行します。

## docker-composeファイルの違い

/docs に詳しくのっています。

### docker-compose.yml

※ 未完成

__todo__

1. coias用dockerアカウントの取得
2. github リポジトリの設定
3. image自動構築設定
4. image pullを行うdocker-compose.ymlの作成

実行用のdocker-composeです。  
アプリケーションの実行のみを行う場合に使用します。  
[実行用環境構築](./docs/実行用環境構築.md)

### docker-compose.dev.yml

開発用のdocker-composeです。  
アプリケーションの開発を行う場合に使用します。  
[開発用環境構築](./docs/開発用環境構築.md)
