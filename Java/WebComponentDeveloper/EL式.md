# EL式

- 使用例
    - 演算式や評価式の結果出力
    - 特定のスコープに格納されたオブジェクトの出力
    - スコープ内に格納されたオブジェクトのプロパティを出力
    - formデータの出力

- 記述方法
    - `${式}`

## 演算子と予約語

|演算子（エイリアス）|説明|
|---|---|
|+|加算|
|-|減算|
|*|乗算|
|/（div）|除算|
|%（mod）|剰余|
|==（eq）|等しい|
|!=（ne）|等しくない|
|<（lt）|小さい|
|>（gt）|大きい|
|<=（le）|以下|
|>=（ge）|以上|
|empty|nullまたは空文字|
|&&（and）|論理積|
| \|\|（or）|論理和|
|!（not）|否定|
|a?b:c|aの場合はb、それ以外はc（三項演算子）|


- .（ドット）
    - オブジェクトのフィールドやマップオブジェクトの要素にアクセスする
- \[\]
    - 配列やコレクションオブジェクトの要素にアクセスする

|予約語|
|---|
|and|
|instanceof|
|false|
|ge|
|eq|
|or|
|empty|
|null|
|gt|
|ne|
|not|
|div|
|true|
|le|
|lt|
|mod|

## EL式が利用可能な場所

- テンプレート要素内に定義
    - `<span>${式}</span>`
    - HTMLのタグ内に直接記述できる
- 他のJSP要素の属性値として定義
    - `<jsp;setProperty value="${式}"/>`

<div style="color:red;">
以下のタグ内に記述するとエラーになる

- スクリプトレット `<% %>`
- 式 `<%= %>`
- 宣言 `<%! %>`

</div>

## 検索順序と暗黙オブジェクトへのアクセス

- 検索の優先順位
1. 暗黙オブジェクトかどうか
    1. 指定されたキーがあるか
    1. ある場合は値を返す。無い場合はnullを返す
1. スコープオブジェクト内を検索
1. nullを返す

### スコープオブジェクトの一覧

|スコープオブジェクト名|説明|
|---|---|
|pageScope|ページスコープのキーと値のマップ|
|requestScope|リクエストスコープのキーと値のマップ|
|sessionScope|セッションスコープのキーと値のマップ|
|applicationScope|アプリケーションスコープにキーと値のマップ|

### 暗黙オブジェクトの一覧

|暗黙オブジェクト名|説明|
|---|---|
|pageContext|PageContextオブジェクト|
|param|String形式のリクエストパラメータのキーと値のマップ|
|paramValues|リクエストパラメータのキーと複数の値を持つString形式の配列のマップ|
|header|HTTPリクエストヘッダーのキーと値のマップ|
|headerValues|HTTPリクエストヘッダーのキーと複数の値を持つString形式の配列のマップ|
|cookie|クッキーのキーと値のマップ|
|initParam|初期化パラメータのキーと値のマップ`<context-param>`|

JSPの暗黙オブジェクトもEL式で使用可能。

使用する際は<span style="color:red;">EL暗黙オブジェクトのpageContext経由</span>でアクセスする。

PageContextクラスにはJSP暗黙オブジェクト用のgetterが実装されているためアクセスできる。

`${pageContext.JSP暗黙オブジェクト}`

## データへのアクセス方法

1. `オブジェクト名.キー名`
1. `オブジェクト名["キー名"]`
    - シングルクォートも可
1. `オブジェクト名.キー名[インデックス]`
1. `オブジェクト名["キー名"][インデックス]`
    - シングルクォートも可

## Function機能の利用

EL式からFunction機能を使ってstaticメソッドを呼び出すことが可能

### Function機能の手順

1. staticメソッドを実装する
1. tldファイルにstaticメソッドの定義をする
1. EL式を使用してstaticメソッドを呼び出す

### tldファイルの作成

作成したtldファイルは`コンテキストルート/WEB-INF`以下へ配置する

```xml
<taglib>
    <functions>
        <name>Functionsの名前</name>
        <function-class>クラス名（完全修飾）</function-class>
        <function-signature>メソッドのシグネチャ</function-signature>
    </functions>
</taglib>
```
### 例
```xml
<taglib>
    <functions>
        <name>boo</name>
        <function-class>hoge.FuncTest</function-class>
        <function-signature>java.lang.String boo(int)</function-signature>
    </functions>
</taglib>
```

### Functionsの呼び出し

- 参照するtldファイルの定義
    - `<%@ taglib uri="tldファイルの場所" prefix="接頭辞" %>`
- 呼び出し
    - `${接頭辞:Functionsの名前（引数）}`