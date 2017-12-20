# AWS Developers Meetup 2017

## DeveloperのためのライブAWSウォークスルー 〜 AWS SDKの使い方 〜

### AWS上でのアプリケーション開発
- サービス操作といえば
    - マネジメントコンソール
    - CLI
- 各サービスの操作はAPIで行なっている
    - APIをコールしているため
    - SDKを使うことで簡単にAPIを呼び出せる
- SDKの種類
    - Python
    - Mobile
    - Java
    - JS
    - .NET
    - Node.js
    - PHP
    - Ruby
    - Go
    - C++
        - 組み込み用途が多い
    - AWS CLI
    - for Eclipse
    - for VS
    - for WindowsPowerShell
- Mobile SDK
    - iOS,Android,FireOS,Xamarin,Unityのライブラリやコードサンプルを提供
    - オープンソース
- Python (boto3)
    - Resource API
        - ２つの異なるレベルのAPIを提供
        - Cliet API（低レベル）はHTTPAPIと1対1でマッピング
        - 2と3どちらにも対応
- AWS Toolkit
    - IDEと統合してより便利な開発ができる
    - Eclipse,VS内でデバッグ可能　確認ができたらpub
- Mobile CLI
    - JSフロント開発者のためにアプリ内でAWSサービスと設定を有効化するためのCLI
    - MobileHubが提供するすべての機能を利用可能
    - MobileCLIは他の業界標準のCLIに準拠するように設計されている
- AWS Amplify
    - クラウド対応のアプリを構築するフロントエンドとモバイル開発者用のJSライブラリ
    - Aws-amplifyライブラリ追加でReactが使えたりする

### 開発を始める前の準備

- AWSへのサインアップ
- ユーザとグループの作成
- AWS CLIのインストールとプロファイルの設定
- AWS SDKのインストール

- 準備が大変な場合はCloud9を
    - クラウド上で開発・テスト・デバッグうぃ完結できるIDE
    - JS,Python,Goなど同根
    - EC2インスタンスを立ち上げてその中で実行している
        - 30分間など一定時間操作が無い場合はインスタンスが停止されるように設定できる
    - デバッグが楽
        - JSはコールスタックも確認できる
- デモコーディングはPython

### まとめ

- SDKを利用することで各サービスをアプリのサービスブロックとして活用できる
- 様々な言語で利用可能、用途に応じて使い分け
- Cloud9は最初から様々な開発言語やツールが同梱されているため始めるのにはオススメ

## ユースケースから見た実装カタログ〜AWS逆引きリファレンス〜

- 対象
    - 実際にどんな設定が必要か
    - 実際にどんなコードを書いたら良いかわからない
- Amplify
    - React ReactNaitiveに対応している
    - できること
        - Auth
        - Analytics
        - API
        - Storage
            - S3
        - Caching など
    - npmでインストール可能
    - オープンソース
        - GitHubにあり
- ユーザ動向を分析したい
- 認証させたい
    - CognitoUserPoolでAuth
        - APIで
        - ReactComponentで
    - Amplifyで各種処理が定義されている
        - サインアップ
        - サインイン
        - サインアウトなど
- 認証つきのAPIを叩きたい
    - 認証後にsigv4で叩きに行く
- Reactを用いたdemo
    - MobileHubも使用

### まとめ
- Amplyfy + MobileCLIで簡単にモバイルアプリの開発が可能に

## RESTful APIをChaliceで紐解く　〜Python Serverless Microframework for AWS

### RESTfulAPIの理解

- RESTはアーキテクチャスタイル
    - プロトコルでは無いため標準の規約はない
    - APIGatewayがサービスの一つ
- 原則
    - クライアント・サーバ
    - ステートレス
    - キャッシュ
    - 統一インタフェース
    - レイヤ化されたシステム
    - コードオンデマンド（Optional）
- コレクションリソース
    - https://api/resources
- エレメントリソース
    - https://api/resources/1

### Chaliceの理解　RESTfulAPIを表現するには

- Chalice
    - Python Serverless Microframework for AWS
    - アプリのコードを書いてデプロイするとAPI GatewayとLambdaを自動で作成更新
    - デコレーターベースのルーティング
    - ローカルでの起動も可能
        - `challice local`
- `@app.route`でRESTfulを表現
    - CORSやAPIキーも表現できる
    - `@app.schedule`で定時起動も可能
- SAMとの違い
    - Chaliceはそれ自体がアプリケーションフレームワーク
        - SAMはCloudFormationの拡張であり構成管理ツールの一種
    - Chaliceはマイクロ志向なので必要最低限の機能を提供

### Chaliceの動作の理解

- Chaliceのファイル構成
    - app.pyに`@app.route()`の実装がある

### 関連情報

- サーバレスで王道フレームワークを使う方法
    - サーバレスでExpress.jsを使う一番簡単な方法
    - Javaの話も

- Domovoi
    - Chaliceを拡張 プラグイン
    - SNSトピック
    - S3イベント
    - Step Function に対応したもの
    - Chliceは拡張しやすいの


