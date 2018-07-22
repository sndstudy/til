# Web Working Group 「PWAに備える3ヶ月」 vol.2

- イベントページ
    - https://japan-android-group.connpass.com/event/85039/

## KotlinJSでServiceWorkerを使ってみた

- 良かった点
    - コードの再利用ができた
- ServiceWorker
    - Proxy
    - Cache
    - Thread can not access DOM
    - Many API
    - indexedDB
- 社内ライブラリStateMachineを移植した
    - StateMachineはデザインパターン
- KotlinはindexedDBの定義がないので定義ファイルを作成する必要があった

## ツールを利用した対応と企業サイドの懸念点

- ECサービスの現場調査
    - 課題
        - モバイルからのコンバージョン率をあげる
        - 顧客ロイヤルティを高める
        - 競合他社からサービス力で差をつける
- ユーザがスマートフォンで利用する時間
    - 主要なアプリ9~16で占められている
- Mobile Centric
- Mobile Extender
- 事例
    - LANCOME
    - 最初はアプリを検討していた
        - 利用頻度が高い人でないと使わない
    - AMPとPWAのハイブリット
        - モバイルのトラフィック
            - 51%向上
        - 直帰率
            - 14%低下
- 検討企業
    - 新規事業との相性
- 導入企業
    - ホームアイコンのみ実装
- 企業からはPWA=Webとそんな変わらないイメージ
    - アプリっぽくないという意見が
- ネイティブアプリよりも少ない工数で実装
    - 既存のWebページを利用
- ベストプラクティス
    - 部分的導入から始める

## お手軽PWA開発環境と近い将来の課題

- お手軽PWA開発環境
    - Create React App
    - Ionic CLI
    - PWA Builder
        - MSが提供している
- Create React App
    - React純正CLI
    - ミニマイズしたSWが付いてくる
- Ionic CLI
    - Ionic純正CLI
    - ベースフレームワークはAngular
    - テンプレート各種
- PWA Builder
    - https://github.com/pwa-builder/ManifoldJS
    - MSの純正ウェブアプリ・CLI
    - 非PWAを読み込んでPWAを出力
    - 各種SWパターン
        - 5つのパターンがある
        - https://github.com/pwa-builder/serviceworkers
    - 各種プラットフォーム最適化出力
- ユーザから見たPWAの心配・不満なところ
    - 見つけにくい?
        - ストアで探しても出てこない
    - そのままではPWAかどうかわかりにくい
        - インストールしようと思わない
        - 特にWebで開いたページなので
    - インストールの操作が面倒・危険な感じがする
        - インストールしないで使い続ける?
    - 動作が遅い・機能が低い
        - ネイティブと比べて。
- アプリ開発者から見たPWA開発の疑問
    - 最適な開発環境は?
        - Webと同じ感覚で開発できる
    - UIフレームワークはどうする?
    - デバイス固有の機能へのアクセスは?
        - https://whatwebcando.today/ で可能かどうか確認できる
    - プラットフォーム固有のフレームワークへのアクセスは?
    - 各種デバイスでのテストは?
- 一般的に考えられるPWAの課題
    - マルウェア対策
    - サニティチェック
    - メモリ、ストレージ使用量の把握・警告、最終通告の受信
    - ユニバーサル性、レスポンシブ性の確保

## 質疑応答・フリートーク

- エンドユーザーからのフィードバックで何かあったか
    - そこまでネガティブな反応はない
    - 採用している企業は出来るならやろう的な感じ
- 他の大手はPWAの開発環境に関してはどんな感じ
    - GoogleはPWAのディベロッパーガイドが充実している
    - PWAに関するライブラリが全然出てきていない
        - 出せば世界的にヒットするかも
