# Dockerイメージとは

- コンテナ実行時に必要なファイルをまとめたファイルシステム
- AUFSなどの特殊なファイルシステム
- イメージ上のでデータはレイヤで構成されている
- 読み取り専用

## Dockerイメージの継承

- CentOSのベースイメージにRubyの実行環境を載せる
  - その上にRoRのイメージを継承することでRoRの実行環境を簡単に作れる
- 継承メリット
  - ベースイメージの2重管理をしなくて良い

## ローカルでのイメージ管理

- `docker images`
  - イメージ一覧
- `docker tag docker/whalesay my_whalesay`
  - イメージにエイリアス付けするコマンド
  - 元となるイメージ、新しいイメージ名の順に記載する
- `docker tag docker/whalesay my_whalesay:ver1`
  - タグ付け
- `docker inspect my_whalesay`
  - イメージの詳細情報を表示するコマンド
- `docker rmi [イメージID]`
    - イメージを削除
    - `-f`オプションを追加することでコンテナが存在している状態でも削除する
- `docker pull docker/whalesay`
  - イメージを取得するコマンド