# Dockerコマンド

- `docker ps`
    - コンテナの一覧を表示
    - `-a`オプションを追加することで停止したコンテナも表示される
- `docker run [イメージ名:タグ]`
    - コンテナを作成し、起動する
    - `--name`オプションでコンテナに名前を付ける
    - `-d`でバックグラウンドでコンテナ実行
    - `-it`でコンテナにログインする。`/bin/bash`か`/bin/sh`でログインする
- `docker start [コンテナ名]`
    - 停止しているコンテナを起動する
- `docker stop [コンテナ名]`
    - 起動しているコンテナを停止する
- `docker rm [コンテナ名]`
    - コンテナを削除する
    - `-f`オプションを追加することでコンテナが起動している状態でも削除する
- `docker exec -it [コンテナ名]`
    - コンテナにログインする。`/bin/bash`か`/bin/sh`でログインする

## イメージ関連のコマンド

- `docker images`
    - イメージの一覧表示
- `docker build -t [タグ名] .`
    - カレントディレクトリにある**Dockerfile**をビルドしてイメージを作成する
- `docker rmi [イメージID]`
    - イメージを削除
    - `-f`オプションを追加することでコンテナが存在している状態でも削除する

## 参考サイト

- [Docker ハンズオン - 基本コマンド編 - Qiita](https://qiita.com/hihihiroro/items/6dda871dc2566801a6da)
- [Dockerイメージとコンテナの削除方法 - Qiita](https://qiita.com/tifa2chan/items/e9aa408244687a63a0ae)