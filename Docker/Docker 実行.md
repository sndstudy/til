# Docker 実行

## 実行の仕組み

1. `docker run hello-world`でhello-worldのDockerイメージを取得して起動する
2. Dockerクライアント(コマンド)がDockerデーモンに接続してhello-worldのイメージを探しにいく
3. PC上にない場合はDockerHubからイメージをダウンロードしてくる
4. ダウンロードしたイメージをもとにコンテナを起動する

※PC上にイメージがある場合は2と3の処理はスキップされる

## docker runが行なっていること

- `docker pull`
  - イメージの取得
- `docker create`
  - コンテナの作成
- `docker start`
  - コンテナの起動

