# coias-docker-compose

coiasの開発環境およびWebアプリを構築します。docker-composeを使用することで、簡単に構築できます。

## ブランチについて

### main

docker hubよりimageのダウンロードを行います。
高速で環境を構築できます。


### image-build

ローカルにてimageのビルドを行います。
時間がかかりますが、imageの開発を行うことができます。

## 環境構築(main)

### coias-docker-composeを任意のディレクトリに展開する

```
git clone https://github.com/aizulab/coias-docker-compose.git
```

### docker-composeの起動

[Docker Desktop for Mac and Windows | Docker](https://www.docker.com/products/docker-desktop)

```
docker-compose up
```

### コードを変更した場合

```
docker-compose build --no-cache
docker-compose up
```
