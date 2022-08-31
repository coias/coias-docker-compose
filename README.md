# coias-docker-compose

coiasの開発環境およびWebアプリを構築します。docker-composeを使用することで、簡単に構築できます。  
docker,docker-composeを使用し、フロントエンドアプリ、バックエンドアプリ、API、webサーバーなどを自動実行します。

## docker-composeファイルの違い

/docs に詳しくのっています。

### docker-compose.yml

実行用のdocker-composeです。  
アプリケーションの実行のみを行う場合に使用します。  
[実行用環境構築](./doc/実行用環境構築.md)

```docker-compose up```

### docker-compose.dev.yml

開発用のdocker-composeです。  
アプリケーションの開発を行う場合に使用します。  
[開発用環境構築](./doc/開発用環境構築.md)
