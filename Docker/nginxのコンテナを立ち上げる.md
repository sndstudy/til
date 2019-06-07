# nginnxのコマンドを立ち上げる

- `docker run --name [コンテナ名] -d -p [ホスト側のポート番号]:[コンテナ側のポート番号] [イメージ名]`

- `-d`
  - デタッチモードでコンテナ実行(バックグラウンドで実行)
  - 指定がないとフォアグラウンドで実行するため、止めるとコンテナも同時に止まる


## 静的ファイルのホスティング

- https://hub.docker.com/_/nginx
- `docker run --name [コンテナ名] -v [ホスト側のディレクトリ]:[コンテナ側のマウントポイント]:[オプション] -d -p [ホスト側のポート番号]:[コンテナ側のポート番号] [イメージ名]`
- `docker run --name some-nginx -v /some/content:/usr/share/nginx/html:ro -d nginx`
- `-v`はボリュームを表す
- `ro`はリードオンリーを表す

