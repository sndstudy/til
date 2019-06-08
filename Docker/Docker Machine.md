# Docker Machineとは

- DockerEngineを搭載した仮想マシンの作成・起動・停止・再起動などをCLIから実行できるツール

## コマンド

- Dockerホストのリストを確認
    - `docker-machine ls`
- Dockerホストの作成(作成後、自動で起動する)
    - `docker-machine create --driver [仮想化のドライバ] [ホスト名]`
    - 仮想化のドライバ
        - どこにDockerのホストを立てるか
        - VirtualBoxの場合は`virtualbox`
    - ホスト名
        - 任意の名前を付けることができる
    - コマンド例
        - `docker-machine create --driver virtualbox default`
- Dockerホストのアクティブ化
     - `docker-machine env [接続したいホスト名]`
     - 接続するための設定コマンドが表示されるのでそのコマンドを打つと接続できる
     - コマンド例
        - `docker-machine env default`
- DockerホストのIP確認
    - `docker-machine ip [ホスト名]`
- Dockerホストの停止
    - `docker-machine stop [ホスト名]`
- Dockerホストの起動
    - `docker-machine start [ホスト名]`
- Dockerホストの切断
    - `docker-machine env -u [切断したいホスト名]`
     - 切断するための設定コマンドが表示されるのでそのコマンドを打つと切断できる 
- Dockerホストの削除
    - `docker-machine rm [削除したいホスト名]`
- Dockerホストへの接続(ssh)
  - `docker-machine ssh [ホスト名]`