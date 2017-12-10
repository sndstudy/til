# Webコンテナのイベント処理

- イベントオブジェクト
    - イベントの情報を含んだオブジェクト。オブジェクトの状態が変化すると発生するオブジェクト。
- リスナーオブジェクト
    - イベントに対する処理を定義したオブジェクト。イベントオブジェクトを受け取る。
- 監視対象オブジェクト
    - ServletContext
    - ServletRequest
    - HttpSession

## ServerContextオブジェクトのイベント処理

ServletContextのイベントオブジェクト

|発生タイミング|イベントクラス|
|---|---|
|生成・破棄|ServletContextEvent|
|属性への追加・変更・破棄|ServletContextAttributeEvent|

ServletContextのリスナーインタフェース

|発生タイミング|リスナーインタフェース|
|---|---|
|生成・破棄|ServletContextListener|
|属性への追加・変更・破棄|ServletContextAttributeListener|

ServletContextListenerのリスナーインタフェースのメソッド

|メソッド名|説明|
|---|---|
|contextInitialized(ServletContextEvent)|オブジェクトが生成された直後に呼ばれるメソッド|
|contextDestroyed(ServletContextEvent)|オブジェクトが破棄される直前に呼ばれるメソッド|

ServletContextAttributeListenerのリスナーインタフェースのメソッド

|メソッド名|説明|
|---|---|
|attributeAdded(ServletContextAttributeEvent)|オブジェクトに属性が追加された直後に呼び出されるメソッド|
|attributeRemoved(ServletContextAttributeEvent)|オブジェクトから属性が削除された直後に呼び出されるメソッド|
|attributeReplaced(ServletContextAttributeEvent)|オブジェクトに保持されている属性が変更された直後に呼び出されるメソッド|

リスナークラスはWebコンテナによってインスタンス化されるためweb.xmlに登録する必要がある。
```xml
<web-app>
    <listener>
        <listener-class>リスナークラス名（完全修飾）</listener-class>
    </listener>
</web-app>
```

## ServerRequestオブジェクトのイベント処理

クラスやインタフェース、メソッド名は`ServletContext`を`ServletRequest`に置き換えればOK