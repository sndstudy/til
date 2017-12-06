# JSPコンフィギュレーション

配備記述子に設定を追加することでWebアプリケーション内にあるJSPで共通して利用する情報を定義することができる。

## `<jsp-config>`タグの直下に配置するタグ

- `<tag-lib>`タグ
    - JSP内で使用するタグライブラリ情報を指定する。
```xml
<taglib>
    <taglib-uri>URI</taglib-uri>
    <taglib-location>tldファイルパス</taglib-location>
</taglib>
```

- `<jsp-property-group>`タグ
    - 複数のJSPをグループ化してそれらのファイルに共通プロパティを指定する


|`<jsp-property-group>`の子タグ|説明|
|---|---|
|url-pattern|プロパティを適用するURLパターンを指定する|
|el-ignored|EL式を無効にするか設定する。trueで有効。デフォルトはfalse|
|page-encoding|文字エンコーディングを設定|
|scripting-invalid|スクリプティングを無効にするか設定する。デフォルトはfalse|
|is-xml|XML形式でのJSPタグに限定する場合はtrueにする。デフォルトはfalse|
|include-prelude|各ページのヘッダーとしてインクルードするファイルを指定する|
|include-coda|各ページのフッダーとしてインクルードするファイルを指定する|
|trim-directive-whitespaces|ディレクティブが宣言された行は空白行としてレスポンスされるがその空白行を削る場合はtrueにする。デフォルトはfalse|
|deferred-syntax-allowed-as-literal|#{}を文字列としてみなすように指定する。デフォルトはfalse|