# OSC 2018 Tokyo Spring

##【入門】Docker入門

cyberblack28
→Qiitaにある

- サーバ仮想化
    - 非仮想化環境
    - ホストOS型仮想
        - VMWare VirtualBox
    - ハイパーバイザー型仮想
        - ホストOSを必要としない
        - Linux KVM
- Linuxコンテナ
    - 仮想マシン、ゲストOSという考えでは無い
    - カーネルの機能によりLinuxで稼働するプロセスをグループに分割して異なる環境を割り当てている
    - コンテナに属さないユーザ空間をホストLinuxという
- Dockerとは
    - Linuxカーネルの機能を統合してコンテナーを作り上げる管理ツール
    - コンテナーを作成するインタフェース
- Dockerイメージ
    - Dockerイメージをコンテナーに割当てることでCentOSやUbuntuをコンテナーで起動することができる
    - DockerHubからpullできる
    - イメージ構造
        - イメージ層
            - コマンドごとに記録
        - ベースイメージ
            - OS
        - コンテナが起動されると自動で書き込み可能なイメージ層が作成される
- コンテナのライフサイクル
- 複数のコンテナ
    - 推奨されるコンテナ利用は1コンテナ1プロセス

## 【入門】機械学習を行うためのPython導入講座

- https://speakerdeck.com/terapyon/ru-men-ji-jie-xue-xi-woxing-utamefalse-pythondao-ru-jiang-zuo
- https://speakerdeck.com/terapyon/python-ji-jie-xue-xi-kotohazime-at-odc

- BootCampのサイトに環境構築の資料がある



