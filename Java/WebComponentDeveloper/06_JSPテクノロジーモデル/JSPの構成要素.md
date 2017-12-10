# JSPの構成要素

## コメント

- 出力コメント 
    - `<!-- コメント -->`
    - 通常のHTMLやXMLのコメントと一緒でWebブラウザに表示される

- 非表示コメント
    - `<%-- コメント -->`
    - Webブラウザには表示されないコメント

## ディレクティブタグ

JSP全体に作用するような定義を行うタグ。
JSP変換時にJSPサーブレットにソースコードが埋め込まれる。

- pageディレクティブタグ
    - `<%@ page 属性="値" %>`
    - `<jsp:directive.page 属性="値" />`
    - JSPファイル全体に関する属性を定義する
    - ページ内の文字コード設定やMIMEタイプを設定する
    - 複数属性を設定する場合はスペースで区切るか1組みずつ複数で書く
    - import
        - JSP内で使用するクラスをインポートする属性。複数の場合はカンマで区切るか複数行で書く
    - session
        - セッション管理に参加するか指定する属性。falseの場合は暗黙オブジェクトのsessionが使用不可になる。
    - contentType
        - レスポンスのMIMEタイプと文字エンコーディングを設定する属性。
    - pageEncoding
        - JSPファイルに記述している文字エンコーディングを設定する属性。デフォルトはcontentTypeのcharsetの値になる
    - isELIgnored
        - JSP内でEL式を使用するか指定する属性。デフォルトはfalseでtrueを指定するとEL式が無視される
    - errorPage
        - 例外が発生するJSPに設定する属性。値には例外が発生した時に遷移するJSPのパスを記載する。
    - isErrorPage
        - エラーページJSPに指定する属性。trueの場合は暗黙オブジェクトのexceptionが使用できるようになる。
    
- includeディレクティブタグ
    - `<%@ include file="ファイルパス" @>`
    - `<jsp:directive:include file="ファイルパス" />`
    - JSPやHTMLのデータを埋め込むときに使用する

- taglibディレクトリ
    - `<%@ taglib prefix="プレフィックス" uri="URI"もしくはtagdir="タグファイルパス" @>`
    - `<jsp:root xmlns:jsp="http://java.sun.com/JSP/Page" xmlns:プレフィックス="URI" version="2.1"></jsp:root>`
    - JSP内でカスタムタグを利用するときに使用する。

## スクリプティング

- スクリプトレット
    - `<% Javaコード %>`
    - `<jsp:scriptlet>Javaコード</jsp:scriptlet>`
    - JSP内で有効なJavaのコードを記述する
    - スクリプトレットで宣言した変数はローカル変数になる
- 宣言
    - `<%! 変数宣言もしくはメソッド定義 %>`
    - `<jsp:declaration>宣言</jsp:declaration>`
    - JSP内のスクリプトで使用する変数やメソッドの宣言を記述する
    - 宣言の形式で記述した変数はインスタンス変数になる
- 式
    - `<%=式 %>`
    - `<jsp:exression>式</jsp:exression>`
    - JSP内のスクリプト内で有効な式を記述する
    - String型として解釈されるため文字列として変換できるコードである必要がある
    - セミコロンは不要

## 暗黙オブジェクト

JSP内でいつでも利用できるオブジェクトのこと

|オブジェクト名|型名|スコープ|
|---|---|---|
|request|ServletRequestのサブクラス|request|
|response|ServletResponseのサブクラス|page|
|pageContext|PageContext|page|
|session|HttpSession|session|
|application|ServletContext|application|
|out|JspWriter|page|
|config|ServletConfig|page|
|page|Object|page|
|exception|Throwable|page|