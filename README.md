# coias-docekr-compose(image-build)

coiasの環境を構築します。

docker,docker-composeを使用し、フロントエンドアプリ、バックエンドアプリ、API、webサーバーなどを自動実行します。

## docker-composeファイルの違い

それぞれの情報は, /docs に詳しくのっています。

* docker-compose.yml

実行用のdocker-composeです。

* docker-compose.dev.yml

開発用のdocker-composeです。

## 必要アプリケーション

下記をインストールすること。

* [Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)

[Remote - Containers - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

* [Docker](https://www.docker.com/products/docker-desktop)

docker のインストール方法は /docs/dockerのインストール.md を見てください。

## 必要ソースのクローンとディレクトリ構成

1. コードのclone

coias-docker-composeを任意のディレクトリに展開する

```
git clone https://github.com/aizulab/coias-docker-compose.git
```

2. ディレクトリ構成

下記のリポジトリをディレクトリに配置する

https://github.com/aizulab/coias_electron.git

https://github.com/Mizunanari/COIAS_program_github.git

```
coias-docker-compose
├── COIAS_program_github   <-- clone
├── coias_electron         <-- clone
├── docker-compose.yml
├── docker-compose.dev.yml
└── READEME.md
```

操作例

```
cd coias-docker-compose
git clone https://github.com/aizulab/coias_electron.git
git clone https://github.com/Mizunanari/COIAS_program_github.git
```

※ private repository の場合は認証の必要あり