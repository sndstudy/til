# Learn Languages 2018 in ODC

- https://llevent.connpass.com/event/95443/
- 開催日
    - 8/26(日)
- 会場
    - 日本工学院専門学校 蒲田キャンパス 3号館7F
- イベント内容
    - “Learn Languages” (複数の言語を学ぼう！) として多種多様なプログラミング言語を取り上げる、プログラミング言語に関する総合カンファレンス

## Language Update (1)

### Java

- スライド
    - https://www.slideshare.net/skrb/learn-language-2018-java-language-update

### Go

- スライド
    - https://docs.google.com/presentation/d/1tirnxqnjo_gdf0GisL4oOmnMknuFxSYQ_9_esnMlZqE/edit#slide=id.p

## Language Update (2)

### PHP

- はじめに
    - リアルワールドでのシェアの割に関心がある人は少ないイメージ
    - WikipediaとかもPHPで作られている
- PHPの開発体制
    - Rasmusは最初の開発者であってBDFLではない
    - PHPの将来を見るにはRFCをチェックする
    - TwitterにRFC Botがある
- 言語特徴
    - ゆるふわにWebアプリが書ける言語
    - 昔ながらのCGIと同じように書ける
        - レンタルサーバ借りてファイルをおけばOK
    - HTMLのテンプレートが書ける
    - PerlっぽいCGIが書ける
    - Javaっぽいクラスが書ける
- 最近の動向
    - PHP7.0からは12月1日前後にリリースされるようになっている
    - 5系の公式サポートが2018年に完全終了となる
    - PHP8にJITが入るかも?
    - PHPStormの普及
        - PHP専用のIDE JetBrains社
    - 言語としては負債を無くそうとする働きが見受けられる

### Python

- はじめに
    - GitHubの中で2番目に多い言語
    - データ分析で人気が出てきている
    - 数値計算・機械学習系のライブラリが豊富
- 最近のアップデート
    - Python3は2008年
        - 10ヶ月周期でリリース 3.7が最新
    - Type hints
        - 引数や関数の戻り値に型注釈をつけることができる
        - 静的解析のための構文のため型チェックは行われない
        - 3.7から型アノテーションの評価がコンパイル時ではなく実行時
    - Data Classes
    - pathlib module
    - GuidoがBDFLを引退

### Ruby

- スライド
    - https://slide.rabbit-shocker.org/authors/znz/language-update-2018-ruby/

### Rust

- スライド
    - https://keens.github.io/slide/rustnokoremadetokorekara/

- 言語特徴
    - システムプログラミング言語
    - 安定性信頼性が売り
    - 2015年に1.0リリース
    - 大体の便利な言語機能を取り入れている
    - 所有権システムによりGCがない
        - 手動でメモリ管理するのではなくコンパイラが自動で管理する
    - 後方互換を大事にしている
        - SemVerベースの管理
    - 学習難易度は難しい
        - その代わり学習補助が手厚い
        - エラーメッセージが親切
    - ドキュメント文化
        - 全ライブラリのドキュメントが用意されている
        - ドキュメントの整備がよくされている
- 開発体制
    - コミュニティベースの開発
    - Mozillaが開発を支援している
        - Mozillaが作って言語ではない
    - RFCで言語機能を決めている
        - 意思決定がオープン
    - 6週間ごとにリリース
    - 4つのWG
        - Network
        - CLI
        - WASM
        - Embed
- Rustのこれから
    - 言語に非互換アップデート入る(Rust2018)
    - 今までのをRust2015,新しいのはRust2018と呼ぶ
    - 互換性はなくなるけど相互運用性はある

## 最近のパッケージマネージャってどれがお勧め？

### C++

- conanというパッケージマネージャーがある
    - でも使いにくい
- conanのパッケージ指定がわかりづらい
    - パッケージの検索方法もわかりづらい
    - Webサイトもわかりづらい
- conanが使いにくいのでpoacというパッケージマネージャを作成している
    - https://github.com/poacpm

### JavaScript

- スライド
    - https://speakerdeck.com/yosuke_furukawa/npm-or-yarn-that-is-a-problem
- npmとyarnどっち使えばいい?
    - どっちもパッケージ管理はできる
- パフォーマンス
    - yarnの方がインストールは速い
    - キャッシュを有効にしてもyarnが速い
    - npm ci
        - ライブラリ取得に特化したサブコマンド
        - 普通のnpm installは裏でゴニョゴニョしている(キャッシュ作ったりなど)
- 特有の機能
    - yarn
        - 依存ライブラリのライセンスが一覧で確認できる機能
        - 依存ライブラリの更新を対話型シェルで行える機能
    - npm
        - npm audit
            - 依存ライブラリで脆弱性が報告されていないか監査する機能
            - npmのサーバ内で監査しているため、yarnには真似できない機能

### Perl

- moduleのインストールにはcpanmを使用する
- 依存moduleの宣言はcpanfileを使用する
- 依存moduleのversionの保存・再現はcartonを使用する

### Python

- 現在はPythonをインストールした時にpipがインストールされる
    - しかしディストリビューションによって無効化されている場合もある
- 環境作成はvirtualenvで作成
- pipの課題
    - インストールしたライブラリの種類を分けられない(開発時のみなど)
- pipenv
    - pipとvirtualenvを両方扱う包括的なツール
    - pipでインストールしてくる(まだPythonと同時にインストールはされない)
    - Python始める人はpipenvから

### Ruby

- スライド
    - https://www.slideshare.net/hsbt/gems-on-ruby-111597452
