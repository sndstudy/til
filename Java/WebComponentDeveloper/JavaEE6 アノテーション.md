# JavaEE6 アノテーション

|@ServletSecurity|||
|@MultipartConfig|||

### @WebServlet

サーブレットのマッピングができる

- name
    - サーブレット名
- urlPatterns
    - マッピングするURLパターン
- value
    - マッピングするURLパターン (urlPatternsがある場合は無効)
- initParams
    - サーブレットの初期化パラメータ
    - `initParams={@WebInitParam(name="name",value="HELLO!!")}`のように指定する
- loadOnStartup
    - サーブレットの開始順序

### @WebFilter

フィルターを設定する

- filterName
    - フィルタ名
- urlPatterns
    - フィルタ対象のURL
- フィルタの順番を指定したい場合は`web.xml`に書く必要がある

### @WebListner

リスナーを設定する

### @ServletSecurity

セキュリティ制約を設けるアノテーション

### @MultipartConfig

ファイルアップロードを使用する際のアノテーション

### 参考サイト

- Tomcat 7も対応したServlet 3.0の6つの主な変更点：Tomcat 7の新機能で何ができるようになるのか？
    - http://www.atmarkit.co.jp/ait/articles/1104/12/news134_2.html
- http://www.oracle.com/technetwork/jp/ondemand/java/jee6-0916ver10-250971-ja.pdf