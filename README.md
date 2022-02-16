coias-docker-compose

coiasの開発環境およびWebアプリを構築

# 環境構築(image-build)

## coias-docker-composeを任意のディレクトリに展開する

```
git clone https://github.com/aizulab/coias-docker-compose.git
```

## ディレクトリ構成

下記のリポジトリをディレクトリに配置する

https://github.com/aizulab/coias_electron.git

https://github.com/Mizunanari/COIAS_program_github.git

```
coias-docker-compose
├── COIAS_program_github   <-- clone
├── coias_electron         <-- clone
├── docker-compose.yml
└── READEME.md
```

操作例

```
cd coias-docker-compose
git clone https://github.com/aizulab/coias_electron.git
git clone https://github.com/Mizunanari/COIAS_program_github.git
```

※ private repository の場合は認証の必要あり

## vscode での操作

下記をインストールする

**必要アプリ**

* [Visual Studio Code](https://azure.microsoft.com/ja-jp/products/visual-studio-code/)

* [Docker](https://www.docker.com/products/docker-desktop)

**必要プラグイン**

* [Remote - Containers - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

## コンテナに接続

Remote Containers(vscode拡張機能)にdocker-composeを読み込ませて、dockerを起動します。
コンテナは「coias-front-app」と「coias-back-app」の2種類を起動します。

1. vscodeの左下にある緑色のリモートウインドウを開きます。
2. Open Folder in Container ...
3. 「coias_electron」フォルダーを選択
4. vscodeを別ウインドウで開き操作を繰り返す
5. 「COIAS_program_github」フォルダーを選択

### imagehostは別途立ち上げる

```
docker-compose -f ./docker-compose.dev.yml up imagehost
```

### 参考

[Get started with development Containers in Visual Studio Code](https://code.visualstudio.com/docs/remote/containers-tutorial)

[既存のDocker開発環境をVS CodeのRemote Developmentで開発できるようにしてみた | DevelopersIO](https://dev.classmethod.jp/articles/add-vs-code-remote-development-settings-to-existing-docker-environment/)

# 備考

キャッシュを使用せずにbuildするコマンド。
git clone がスキップされない。

```
docker-compose build --no-cache
docker-compose up
```
