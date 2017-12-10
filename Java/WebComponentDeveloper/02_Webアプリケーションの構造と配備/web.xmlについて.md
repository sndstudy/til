# web.xmlについて

## web.xmlのタグルール

- ルートタグを必ず記述する
```xml
<web-app></web-app>
```

- 開始タグと終了タグを必ず記述する
- web.xml内は大文字小文字が区別される

## サーブレットの登録と呼び出し

- サーブレットの登録
```xml
<servlet>
    <servlet-name>サーブレット名</servlet-name>
    <servlet-class>サーブレットクラス名（完全修飾）</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>サーブレット名</servlet-name>
    <url-pattern>マッピングするURLパターン</url-pattern>    
</servlet-mapping>
```

- サーブレットの呼び出し

`http://<ホスト名>:<ポート番号>/<コンテキストルート>/<URLパターン>`

例)http://localhost:8080/WebApp/mainpage
- ホスト名
    - localhost
- ポート番号
    - 8080
- コンテキストルート
    - WebApp
- URLパターン
    - mainpage

## URLパターンの指定方法
- /testで実行される(/から始まる指定)
```xml
<url-pattern>/test</url-pattern>
```
- /test/aや/test/bで実行される(/で始まり*で終わる指定)
```xml
<url-pattern>/test/*</url-pattern>
```
- /test.doや/test/hoge.doで実行される(*.による指定)
```xml
<url-pattern>*.do</url-pattern>
```

## URLパス情報の取り出し
- HttpServletRequestのインタフェース

|メソッド名|説明|
|---|---|
|StringBuffer getRequestURL()|プロトコルとサーバ名とポート番号とサーバのパスが含まれるリクエストURLを返却|
|String getContext()|コンテキストルートだけを返却|
|String getServletPath()|サーブレットを呼び出し部分だけを返却|
|String getPathInfo()|拡張パスを返却（サーブレットの呼び出し部分以降を返却）|

例）http://localhost:8080/WebApp/main/hogehoge

- getRequestURL
    - http://localhost:8080/WebApp/main/hogehoge
- getContext
    - /WebApp
- getServletPath
    - /main
- getPathInfo
    - /hogehoge

## サーブレットの起動設定
```xml
<servlet>
    <servlet-name>サーブレット名</servlet-name>
    <servlet-class>サーブレットクラス名（完全修飾）</servlet-class>
    <load-on-startup>順番</load-on-startup>
</servlet>
```
- `<servlet-class>`の代わりに`<jsp-file>`を指定すると特定のJSPをコンテナ起動時にインスタンス化される

## ウェルカムページの設定
```xml
<web-app>
    <welcome-file-list>
        <welcome-file>ファイル名1</welcome-file>
        <welcome-file>ファイル名2</welcome-file>
        <welcome-file>ファイル名3</welcome-file>
    </welcome-file-list>
</web-app>
```
- 複数ファイル設定可能。上からファイルが検索される。

## エラーページの設定
- HTTPステータスコードによる指定
    - ソースコードではHttpServletResponseインタフェースの`sendError()`で遷移させることができる。引数はステータスコード。
```xml
<web-app>
    <error-page>
        <error-code>ステータスコード</error-code>
        <location>ファイル名</location>
    </error-page>
</web-app>
```

- Javaの例外クラスによる指定
```xml
<web-app>
    <error-page>
        <exception-type>例外クラス名（完全修飾）</exception-type>
        <location>ファイル名</location>
    </error-page>
</web-app>
```

## MIMEタイプの追加
```xml
<web-app>
    <mime-mapping>
        <extension>拡張子（.は不要）</extension>
        <mime-type>MIMEタイプ</mime-type>
    </mime-mapping>
</web-app>
```
## 環境リソースとEJBコンポーネントの参照設定
- `<resource-ref>`は外部リソースへの参照を定義している
```xml
<web-app>
    <resource-ref>
        <res-ref-name>リソースの参照名</res-ref-name>
        <res-type>リソースのクラス名</res-type>
        <res-auth>リソースの制御方法</res-auth>
    </resource-ref>
</web-app>
```
例)

```xml
<web-app>
    <resource-ref>
        <res-ref-name>jdbc/mysql</res-ref-name>
        <res-type>javax.sql.DataSource</res-type>
        <res-auth>CONTAINER</res-auth>
    </resource-ref>
</web-app>
```

- `<resource-env-ref>`はリソース環境への参照を定義している
```xml
<web-app>
    <resource-env-ref>
        <resource-env-ref-name>リソースの参照名</resource-env-ref-name>
        <resource-env-ref-type>リソースのクラス名</resource-env-ref-type>
    </resource-env-ref>
</web-app>
```
例)

```xml
<web-app>
    <resource-env-ref>
        <resource-env-ref-name>jms/Test</resource-env-ref-name>
        <resource-env-ref-type>javax.jms.Queue</resource-env-ref-type>
    </resource-env-ref>
</web-app>
```

- `<env-entry>`は環境エントリへの参照を定義している
```xml
<web-app>
    <env-entry>
        <env-entry-name>環境エントリ名</env-entry-name>
        <env-entry-value>環境エントリの値</env-entry-value>
        <env-entry-type>環境エントリの型</env-entry-type>
    </env-entry>
</web-app>
```
例)

```xml
<web-app>
    <env-entry>
        <env-entry-name>test/string</env-entry-name>
        <env-entry-value>Hello</env-entry-value>
        <env-entry-type>java.lang.String</env-entry-type>
    </env-entry>
</web-app>
```

## EJBコンポーネント参照情報の登録
- `<ejb-ref>`はEJBクライアントからのアクセスがリモートでの参照の場合
```xml
<web-app>
    <ejb-ref>
        <ejb-ref-name>EJBの参照名</ejb-ref-name>
        <ejb-ref-type>EnterpriseBeanの種類</ejb-ref-type>
        <home>リモートホームの型</home>
        <remote>リモートの型</remote>
        <ejb-link>EJBオブジェクト名</ejb-link>
    </ejb-ref>
</web-app>
```
- `<ejb-local-ref>`はEJBクライアントからのアクセスがローカルでの参照の場合
```xml
<web-app>
    <ejb-local-ref>
        <ejb-ref-name>EJBの参照名</ejb-ref-name>
        <ejb-ref-type>EnterpriseBeanの種類</ejb-ref-type>
        <local-home>ローカルホームの型</local-home>
        <local>ローカルの型</local>
        <ejb-link>EJBオブジェクト名</ejb-link>
    </ejb-local-ref>
</web-app>
```