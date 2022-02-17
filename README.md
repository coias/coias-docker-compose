# coias-docekr-compose(image-build)

coiasの環境を構築します。

docker,docker-composeを使用し、フロントアプリ、バックアプリ、API、webサーバーを自動実行します。

## docker-composeファイルの違い

* docker-compose.yml

実行用のdocker-composeです。

* docker-compose.dev.yml

開発用のdocker-composeです。

## 必要アプリケーション

下記をインストールすること。

### mac windownの場合

* docker desktop

[Docker Desktop for Mac and Windows | Docker](https://www.docker.com/products/docker-desktop)

### Linux(例：ubuntu)の場合

* docker engine
* docker compose

[UbuntuにDockerEngineをインストールする| Dockerドキュメント](https://docs.docker.com/engine/install/ubuntu/#upgrade-docker-after-using-the-convenience-script)

[Docker Compose のインストール — Docker-docs-ja 19.03 ドキュメント](https://docs.docker.jp/compose/install.html#linux-compose)

# 開発環境構築(docker-compose.dev.yml)

ここでは開発環境の構築について解説します。

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

3. vscode での操作

下記をインストールする

**必要アプリ**

* [Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)

* [Docker](https://www.docker.com/products/docker-desktop)

**必要プラグイン**

* [Remote - Containers - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

4. コンテナに接続

Remote Containers(vscode拡張機能)にdocker-composeを読み込ませて、dockerを起動します。
コンテナは「coias-front-app」と「coias-back-app」の2種類を起動します。

      1. vscodeの左下にある緑色のリモートウインドウを開きます。
      2. Open Folder in Container ...
      3. 「coias_electron」フォルダーを選択
      4. vscodeを別ウインドウで開き操作を繰り返す
      5. 「COIAS_program_github」フォルダーを選択

5. imagehostを別途立ち上げる

```
docker-compose -f ./docker-compose.dev.yml up imagehost
```

### 参考

[Get started with development Containers in Visual Studio Code](https://code.visualstudio.com/docs/remote/containers-tutorial)

[既存のDocker開発環境をVS CodeのRemote Developmentで開発できるようにしてみた | DevelopersIO](https://dev.classmethod.jp/articles/add-vs-code-remote-development-settings-to-existing-docker-environment/)

# 環境構築(docker-compose.yml)

1. コードのclone

coias-docker-composeを任意のディレクトリに展開する

```
git clone https://github.com/aizulab/coias-docker-compose.git
```

2. docker-compose up

```
dcoekr-compose up
```

# 備考

キャッシュを使用せずにbuildするコマンド。
git clone がスキップされない。

```
docker-compose build --no-cache
docker-compose up
```
