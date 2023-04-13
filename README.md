# coias-docker-compose

coias の開発環境および Web アプリを構築します。docker-compose を使用することで、簡単に構築できます。  
docker,docker-compose を使用し、フロントエンドアプリ、バックエンドアプリ、API、web サーバーなどを自動実行します。

## docker-compose ファイルの違い

/docs に詳しくのっています。

## 必要事項

- https://drive.google.com/drive/folders/1reoBxS-flvlzH1cV9r23htTC_N2RyTaH?usp=share_link
- ここから sql.zip を、coias-docker-compose/直下に解凍して配置する。アクセス権限が必要なため、開発環境動かしたい方権限リクエストをお願いします。

### docker-compose.yml

実行用の docker-compose です。  
アプリケーションの実行のみを行う場合に使用します。  
[実行用環境構築](./doc/実行用環境構築.md)

`docker-compose up -d`

のみで立ち上がります。

### docker-compose.dev.yml

開発用の docker-compose です。  
アプリケーションの開発を行う場合に使用します。  
[開発用環境構築](./doc/開発用環境構築.md)

開発環境を整えます。

検証をする場合はこちらになります。
