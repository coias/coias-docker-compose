# COIASローカル開発環境 起動・停止手順

対象は `coias-docker-compose` のローカル Docker 開発環境(`docker-compose.dev.yml`)のみ。
本番環境の操作には適用しないこと。

## 構成とURL対応表

| コンテナ(サービス名)                          | 役割                    |
| ----------------------------------------------- | ----------------------- |
| coias-mysql (mysql)                             | DB                      |
| coias-keycloak (keycloak)                       | 認証                    |
| coias-docker-compose-imagehost-dev-app-1 (imagehost-dev-app) | 画像ホスト |
| coias-back-dev-container (back-dev-app)         | バックエンド(FastAPI)   |
| coias-front-dev-container (front-dev-app)       | メインアプリ(React)     |
| coias-front-page-dev-container (front-dev-page) | フロントページ(React)   |

| 用途                | URL                             |
| ------------------- | -------------------------------- |
| フロントページ/ログイン | `http://localhost:3001/login`  |
| メインアプリ         | `http://localhost:3000/app/`     |
| バックエンドの疎通確認 | `http://localhost:8000/status` |
| Keycloak            | `http://localhost:8080/auth`     |
| 画像ホスト           | `http://localhost:8088`          |

## 起動手順

### 1. コンテナを起動する

初回、またはコンテナを `stop` していた場合は `coias-docker-compose` ルートで実行する。

```bash
docker compose -f docker-compose.dev.yml up -d mysql keycloak imagehost-dev-app
docker compose -f docker-compose.dev.yml up -d back-dev-app
docker compose -f docker-compose.dev.yml up -d front-dev-app
docker compose -f docker-compose.dev.yml up -d front-dev-page
docker compose -f docker-compose.dev.yml ps
```

mysql と keycloak が起動してから backend を起動すること。
(すでに `docker start` 済みで単に一部のコンテナだけ止まっている場合は、該当コンテナのみ `docker start <コンテナ名>` でよい)

### 2. アプリケーションプロセスを起動する

各コンテナは `tty: true` で起動するだけで、中の FastAPI / yarn start は自動起動しない。
そのため、コンテナを新規に作り直した直後や、プロセスごと止めていた場合は手動で起動が必要。

一度起動すれば、そのコンテナを停止・削除しない限りプロセスはバックグラウンドで動き続ける
(VSCode を閉じても生き続ける)。そのため、コンテナが起動済みでプロセスも生きていれば、
この手順2は不要。

- **バックエンド**(`web-coias-back-app`): VSCode の「実行とデバッグ」→ **COIAS FastAPI** で起動、または以下を手動実行

  ```bash
  source /root/miniconda3/etc/profile.d/conda.sh
  conda activate coias
  python -m uvicorn API.main:app --host 0.0.0.0 --reload
  ```

- **メインアプリ**(`web-coias-front-app`): VSCode の「実行とデバッグ」→ **yarn start**、または `/home/COIASusers/web-coias-front-app` で `yarn start`

- **フロントページ**(`web-coias-front-page`): `/home/COIASusers/web-coias-front-page` で `yarn start`

  ※ front-page の開発サーバーはポート3001で待ち受ける。チェックイン済みのデバッグ設定名にポート3000と書かれている場合があるので、確認は必ず `http://localhost:3001/login` を明示的に開くこと。

### 3. 動作確認

1. `http://localhost:8000/status` にアクセスしてバックエンドの応答を確認
2. `http://localhost:3001/login` からログインし、メインアプリ(`http://localhost:3000/app/`)へ遷移できることを確認
   (別タブで直接3000番を開くとログイン状態が引き継がれないため、必ずログインページから始める)

フロントのみの軽微な文言修正等を確認したいだけであれば、該当するフロント(front-app / front-page)のURLを開くだけでよい。

## 停止手順

数日以上ローカルで開発する予定がない場合は、コンテナを停止しておくとよい。
(Apple Silicon Mac 環境では x86 イメージを QEMU エミュレーションで動かしているため、CPU・メモリ消費が大きい)

```bash
docker compose -f docker-compose.dev.yml stop
```

- `stop` はコンテナを削除しないため、次回は「起動手順」の `docker start` 相当(`up -d`)から再開できる。
- `down` (コンテナ削除)まで行う必要はない。
- データは消えないので安心してよい。
  - MySQLのデータ: `./mysql_data` (bind mount)
  - node_modules: `app_node_modules_volume` / `page_node_modules_volume` (named volume)

再開するときは、本手順の「起動手順」を最初から実行する
(コンテナ起動 → 必要であればアプリケーションプロセス起動 → 動作確認)。

## トラブルシューティング

- **ログインできない**: mysql・keycloak が起動しているか確認 → backend の起動を確認 → `http://localhost:3001/login` から確認をやり直す。原因が特定できるまでパスワードのリセットはしない。
- **フロントの変更が反映されない**: 該当する `yarn start` プロセスを完全に停止し、起動し直す(翻訳ファイルなど一部の変更はホットリロードが効かないことがある)。
- その他の詳細な構築手順・トラブル対応は [開発用環境構築](開発用環境構築.md) も参照。
- このリポジトリには `.claude/skills/coias-dev-environment` に Claude Code 向けの詳細な手順書もある。
