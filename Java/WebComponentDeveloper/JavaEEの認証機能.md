# JavaEEの認証機能

## 情報セキュリティ
- 機密性
    - 権限によってリソースへのアクセス制限がされている
- 完全性
    - データの正当性・一貫性を維持すること。改ざんやデータの欠落がされていないという特性
- 可用性
    - いつでも正常なサービスを提供できる状態を維持するという特性

## 認証方式

|認証方式|説明|
|---|---|
|BASIC認証|HTTPヘッダーを利用。ブラウザのダイアログボックスを使用してユーザ名、パスワードを送信する。送信データはBASE64で符号化されているだけで暗号化はされていない。|
|DIGEST認証|HTTPヘッダーを利用。ブラウザのダイアログボックスを使用してユーザ名、パスワードを送信する。送信データは暗号化される。|
|FORM認証|ログインページと認証失敗時のエラーページを作成する。送信データは暗号化されない。|
|CLIENT-CERT認証|SSL上の暗号化が前提。クライアント証明証を利用した認証方式。事前にブラウザにデジタル証明書がインストールされている必要がある。|

## web.xmlによるセキュリティ設定

|定義内容|タグ名|説明|
|---|---|---|
|ロール|`<security-role>`|ロール名を定義する。ロール名はあらかじめ`conf\tomcat-users.xml`で定義していないと使用できない。|
|認証方式|`<login-config>`|認証タイプを定義する|
|セキュリティ制約|`<security-constraint>`|認証が必要な情報資産の範囲とロールを定義する|

- `<security-role>`タグ
    - 複数の場合は複数のタグセットを記載する

```xml
<web-app>
    <security-role>
        <role-name>ロール名</role-name>
    </security-role>
</web-app>
```

- `<login-config>`タグ
    - FORM認証は`<form-login-config>`タグが必要になる
    - ファイルパスはコンテキストルートからの相対パスを指定する

```xml
<web-app>
    <login-config>
        <auth-method>認証方式</auth-method>
        <realm-name>領域名（省略可）</realm-name>
        <form-login-config>
            <form-login-page>ログインページ名</form-login-page>
            <form-error-page>エラーページ名</form-error-page>
        </form-login-config>
    </login-config>
</web-app>
```

- `<security-constraint>`タグ
    - 保護レベル

    |定義内容|説明|
    |---|---|
    |NONE|セキュリティを要求しない|
    |INTEGRAL|データが改ざんされていないことを要求（完全性）|
    |CONFIDENTIAL|盗聴されていないことを要求（機密性）|

```xml
<web-app>
    <security-constraint>
        <web-resource-collection>
            <web-resource-name>情報資産の範囲名</web-resource-name>
            <url-pattern>URLパターン</url-pattern>
            <http-method>HTTPメソッド</http-method>
        </web-resource-collection>
        <auth-constraint>
            <role-name>ロール名</role-name>
        </auth-constraint>
        <user-data-constraint>
            <transport-guarantee>保護レベル</transport-guarantee>
        </user-data-constraint>
    </security-constraint>
</web-app>
```

## セキュリティ情報の取得
- HttpServletRequetインタフェースでメソッドが提供されている

|メソッド名|説明|
|---|---|
|String getAuthType()|認証方式の名前を返却する|
|String getRemoteUser()|認証されているユーザ名を返却する|
|boolean isUserInRole(String)|認証されているユーザが引数で指定したロールに含まれているかを返却する|
|java.security.Principal getUserPrincipal()|認証されているユーザ名を含むオブジェクトを返却する|