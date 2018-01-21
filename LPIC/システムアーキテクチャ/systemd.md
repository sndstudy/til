# systemd

### 概要

systemdを採用したシステムではsystemdプロセスが起動し、各種サービスを管理する。

システムの起動処理は多数の**Unit**と呼ばれる処理単位に分かれている。Unitはいくつかの種類に分類され、拡張子で種類を区別できる。「httpd.service」はhttpdサービスの起動に使用されるUnitとなる。

|拡張子|説明|
|---|---|
|service|各種サービスを起動する|
|device|各種デバイスを表す|
|mount|ファイルシステムをマウントする|
|swap|スワップ領域を有効にする|
|target|複数のUnitをグループ化する|

systemdでは必要なサービスのみ起動する。　また、サービスの起動は並列的に行われるため順次起動するSysVinitと比べて起動時間が短い。

### 起動手順

システムを起動するとまず**default.target**というUnitが処理される。このUnitの設定ファイルは`/etc/systemd/system`ディレクトリ以下にある。

**graphical.target**とはグラフィカルログイン（ランレベル5）で起動するサービスをまとめたUnitです。グラフィカルログインをデフォルトにするには`/lib/systemd/system/graphical.target`へのシンボリックリンクを**default.target**を作成する。

- シンボリックリンク作成例
    - `ln -s /lib/systemd/system/graphical.target /etc/systemd/system/default.target`

|ランレベル|ターゲット|
|---|---|
|0|poweroff.target|
|1|rescue.target|
|2,3,4|multi-user.target|
|5|graphical.target|
|6|reboot.target|

### systemctlによるサービスの管理

systemdでサービスを管理するには`systemctl`コマンドを使用する。

`systemctl サブコマンド [Unit名] [-t 種類] `

|サブコマンド|説明|
|---|---|
|start|サービスを起動する|
|stop|サービスを終了する|
|restart|サービスを再起動する|
|reload|サービスの設定を再読み込みする|
|status|サービスの稼働状態を表示する|
|is-active|サービスが稼働しているか確認する|
|enable|システム起動時にサービスを自動起動する|
|disable|システム起動時にサービスを自動起動しない|
|list-unit-files|全てのUnitを表示する|
|reboot|システムを再起動する|
|poweroff|システムをシャットダウンする|

