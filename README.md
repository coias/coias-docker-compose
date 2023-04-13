# coias-docker-compose

coias の開発環境および Web アプリを構築します。docker-compose を使用することで、簡単に構築できます。  
docker,docker-compose を使用し、フロントエンドアプリ、バックエンドアプリ、API、web サーバーなどを自動実行します。

## docker-compose ファイルの違い

/docs に詳しくのっています。

## 必要事項

- https://drive.google.com/drive/folders/1reoBxS-flvlzH1cV9r23htTC_N2RyTaH?usp=share_link
- ここから sql.zip を、coias-docker-compose/直下に解凍して配置する
- アクセス権限が必要なため、開発環境動かしたい方権限リクエストをお願いします。

## うまく動かない場合

- docker-compose 時に生成される、coias-docker-compose/mysql_data を削除し、
- 関連の image, container, volume を削除してもう一度 docker compose up -d

### docker-compose.yml

実行用の docker-compose です。  
アプリケーションの実行のみを行う場合に使用します。  
[実行用環境構築](./doc/実行用環境構築.md)

`docker-compose up -d`

### docker-compose.dev.yml

開発用の docker-compose です。  
アプリケーションの開発を行う場合に使用します。  
[開発用環境構築](./doc/開発用環境構築.md)
