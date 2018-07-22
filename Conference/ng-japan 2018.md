# ng-japan 2018

- イベントページ
    - https://ngjapan.org/

## Keynote

- 2017年の時点で開発者が100万人を越えた
    - コミュニティが成長している
- angular.ioの30日間のアクセス数が140万
- 790以上の meetup開催　世界中で
    - 53万人のメンバー
    - 東京でも開催予定
- Angular Material
    - datepickerのヘッダーカスタマイズ可能
    - Material Designのコンポーネントがどんどん追加されている
    - virtual scrolling
- `ng update`でcoreやTypeScriptを更新できる
- `ng add`でAngularライブラリインストール、package.json追記、AppModuleにインポートされる
    - `ng add @angular/material`
    - ng addに対応してるのは、angular公式どころと ng-bootstrap,clarity,nativescript
- https://update.angular.io/
    - Angularのアップデート方法を教えてくれるサイト
- Project Ivy のコンセプト
    - Smalller
    - Faster（新しいレンダリングパイプラインによる）
    - Simpler
    - 他のビューライブラリに組み込みやすくなるかも?
        - jQuery
        - React
        - Vue etc

## AngularでPWAを進める

- Service Workerは翻訳済み

- UXからみたPWA
    - PWAの定義があまり定まっていない
        - ユーザに価値を届けるという点ではブレていない
    - デスクトップにアイコンが表示される
        - ヘッダーフッターがなくなり全画面表示になる
            - ブラウザの操作ができなくなる（戻るなど）
    - キャッシュはアプリ側に近い方が速い
    - ServiceWoke
        - HTTPキャッシュをJSでできるようにしたもの
        - ネットワークのプロキシ
    - push通知
    - スマホ・タブレット・PCにインストール可能
- AngularのPWAとは
    - SPA+PWAでフルクライアントアプリケーション
    - Package
        - `@angular/service-worker`
            - 実行モジュール
                - キャッシュ取得やアプリのバージョン管理をする
        - `@angular/pwa`
            - コード生成補助ツール
            - manifest.jsonの生成 など
    - キャッシュリソースはjsonで指定する
        - 対象リソース
        - キャッシュ有効期限
        - ServiceWorkerスクリプトコードは書かなくて良い
        - ng buildする度にjsonファイルが更新される
        - cashfirst
            - キャッシュを優先する
            - アバター画像に有効
        - networkfirst
            - ネットワークを優先
            - タイムアウトの場合のみキャッシュ使う
- これからどうなるのか
    - まずはbetter web app
        - 正直iPhoneが追いついていない
            - window.opne類の処理が入るとSafariに飛ばされる
            - webstrageやcookieがブラウザと別になる
    - Angularはフルクライアントアプリからマッシュアップになっていく
        - Ivy + Elements = WebComponents
        - SPAがコラボレートWebAppになる
    - オフラインアプリの可能性
    - デバイスを越えたアプリ
        - クライアント機能はデバイスで普及し、Webの技術が発展すると輸入される
            - Socket→WebSocketなど

## Angular活用実績から、ハマり事例のご紹介

- プロジェクト特徴
    - 大規模 画面が数百
    - 中国オフショア開発
    - 品質
- 品質への期待
    - ミッションクリティカル
    - 24/365
    - 画面デザインへのこだわり
    - BtoCが多い
        - 起動したSPAを長時間使用する
        - 起動時の時間は考慮しない(少し時間がかかっても良い)
- 役割分担失敗
    - 課題
        - フロントエンドの重要度が増す
            - 従来はJavaだったのでフロントエンド技術者が不足している
            - 対策としてPL/BLが疎結合なのでPLを別チームで開発
                - インターフェースに注意
                - PLの重要度に応じて要員を調達する
- 迷子の開発者
    - 実装方法のバリエーションが多いから迷う
    - 予め処理の方法やタイミングを決める
        - 処理方式
        - データの受け渡しの方法
        - 画面遷移パターン
        - 業務チェックのタイミング etc
    - メリット
        - 誰が作っても同じ構成のコード
        - レビューしやすい
        - 保守しやすい
        - 実装方法を共有できる
    - 理想はコピペできるサンプルコード集
    - 執拗な標準化が必要
- オフショア教育
    - 5,10人くらいなら対面で伝えられる
    - そもそもJava技術者にAngularを学んでもらう必要があった
    - 雪だるま式教育法
        - リーダたちに研修を実施
        - 研修ごと持ち帰ってもらい内部で展開していく
    - コンテンツだけではなく育成の仕組みを作っていく
- メモリリークとの戦い
    - SPAを立ち上げたまま長時間使い続ける業務
        - メモリ使用量が2.5時間で1GB増
    - 対策
        - SPA分割
            - 一連の業務が完了した時点でSPAを再読み込みしてしまう
            - 業務のまとまり毎にSPAを作成
        - メモリリークを発生しやすい箇所を局所化
            - メモリリークの発生が高い実装は共通部品を作って開発者に作らせない
            - DOMリークがよくある例
            - サードパーティライブラリ
                - ページリロード向けに作成されていることが多い
    - メモリリーク抑止のために標準化が前提

## Angularで新サービス作って学んだこととか

- 作っているサービス
    - SpotSale
- 使ってみてよかったこと
    - HTMLベースのテンプレート
        - デザイナーさんが直接編集しやすい
        - 分業しやすい
    - TypeScript
    - SPA
        - 動き出した早い
- イマイチなところ
    - ビルドに時間がかかる
        - 特にSSR用のビルドが時間かかる
    - SSRで謎のエラー
- 困ったことなど
    - ページ切り替え時にページの先頭が表示されない
        - 別ページに遷移した時、スクロール位置がそのまま
            - 画面遷移時にスクロール位置をリセットする
    - 複数アプリケーションを効率よく管理したい
        - ユーザ・店舗向け・管理者向けがある
            - AngularCLI6で **multiple projects** を用いて管理ができる
        - 複数アプリのデプロイ
            - パスを分ける
                - `--base-href`
- 新しいバージョンをデプロイ後リロードしないと反映されない
    - アプリ内でページを切り替えても新バージョンにならない
        - 定期的にアプリのバージョンをチェックする
- 必要だったサーバーサイドレンダリング
    - https://github.com/angular/angular-cli/wiki/stories-universal-rendering
    - Angular Universal Starterをベースにすると楽にSSRできる
        - https://github.com/angular/universal-starter

## Screenshot test in Angular

https://speakerdeck.com/quramy/screenshot-testing-with-angular?slide=1

- View層のテストが難しい
    - DOMのassertが壊れやすい
    - JestやAvaもあるけどAngularと相性が悪い
        - CSSに対するテストには効果がない
- 画像で比較を行う
    - 差分比較
- 使用するツール
    - Storybook
        - コンポーネントをhtml化する
    - Puppeteer
        - キャプチャを取得する
        - ヘッドレスブラウザの一種
        - 裏はChrome
    - reg-suit
        - Gitのコミット履歴からどの画像と比較するのか

## Protractor under the hood

- Protractor
    - e2eテストに必要なお膳立てをしてくれるフレームワーク
    - 担当する範囲はブラウザとテストコード

## AngularとPlantUMLを組み合わせ表現力を更に上げる

- 悩み
    - 設計書・仕様書が様々なアプリで作られている
        - 視覚的な表現が自由に行われるため非常に効果的
            - しかし、更新や追加をするとき変更点がわかりにくくなる
        - 障害対応や緊急時は設計書への変更・反映が後回しになってしまう
            - 実装と離れてしまう
- ExcelやPP以外に何かあるか？
    - PlantUMLが候補に上がった
        - Angularと組み合わせることに成功
            - 図を書いたり参照したりするのはブラウザ上で可能にした
            - 専用ツールが不要
- 工夫点・考慮点
    - PlantUMLサーバーの用意
        - Dockerでサーバーを立ち上げた

## AngularアプリケーションにおけるCSS設計手法

- なぜCSS設計が必要か
    - 名前空間がない
    - 価の再利用が難しい
- AngularにはどんなCSSがあるか
    - Component CSS
        - 1つのコンポーネントに対して使われるCSS
    - Shared CSS
        - 複数のコンポーネントに対して共通のCSS
    - Global CSS
        - 全コンポーネントに対して適用されるCSS
        - Angularではstyle.css
- 使い分け
    - Component CSS
        - 基本はこれで書いていく
        - 名前空間は使わず本質的でシンプルな名前を使う
    - Shared CSS
        - 多くなった場合は再設計を検討する
- どう値を共通化していくか
    - Sassを使用する
        - 変数
        - Mixin
    - 変数
        - 色や数値に関するもの。
        - 変数の上書きは禁止。全ファイルで読み込む変数はユニークな名前にする
        - 変数名がドキュメントになるイメージ
    - Mixin
        - まとまった単位でのstyleのセットを共通化する場合
- CSSのマインド
    - 半年後にすぐに消せるコードを書くこと
    - CSSのコードは一番変わりやすい

## Angular CDK

- Angular CDK
    - material.angular.io/cdk/
- Angular Material
    - material.angular.io
- デモ
    - https://stackblitz.com/edit/text-input
    - text-inputというコンポーネントを作成している

## Angular Ivy

- 小さい
- 速い
- シンプル
- レンダリングの部分を改善する？
