# Dockerのインストール

Dockerのインストール方法です。

## macの場合

homebrewをインストールしているのであれば、homeberwでインストールするのが良いです。

### homebrewを使用する場合

homebrewがインストール済みであることが条件です。

```zsh
brew install --cask docker
```

DockerをLaunchpadから起動します。

## windownの場合

まず、下記のアプリケーションをインストールします。

[Docker Desktop](https://www.docker.com/products/docker-desktop)

インストール後にDocker Desktopが動作しない場合は、再起動を行なってください。

**参考**

[VisualStudioCodeリモート開発を使用したコンテナー内での開発](https://code.visualstudio.com/docs/remote/containers#_installation)

[Install Docker Desktop on Windows](https://docs.docker.com/desktop/install/windows-install/#install-docker-desktop-on-windows)

### エラーが表示される場合

パッケージが最新ではないとエラーが表示されます。

![image](/doc/image/docker-install-3.png)

上記エラーが表示される場合は、[こちらのリンクから](https://docs.microsoft.com/ja-jp/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)**x64 マシン用 WSL2 Linux カーネル更新プログラム パッケージ**をインストールしてください。アプリケーションまたはPCの再起動が必要なら行います。

![image](/doc/image/docker-install-4.png)

## Linux(例：ubuntu)の場合

2022/08/31　追記　Linux版のDocker Desktopが公開されました。下記のリンクからダウンロードしてください。その他の操作は必要ありません。

[Docker Desktop](https://www.docker.com/products/docker-desktop)

ubuntuの場合は下記のスクリプトが使用できる。
dockerを使用する際に`sudo`が必要になる。

* docker engine
* docker compose

[UbuntuにDockerEngineをインストールする| Dockerドキュメント](https://docs.docker.com/engine/install/ubuntu/#upgrade-docker-after-using-the-convenience-script)

[Docker Compose のインストール — Docker-docs-ja 19.03 ドキュメント](https://docs.docker.jp/compose/install.html#linux-compose)

## 公式Doc

[VisualStudioCodeリモート開発を使用したコンテナー内での開発](https://code.visualstudio.com/docs/remote/containers#_installation)