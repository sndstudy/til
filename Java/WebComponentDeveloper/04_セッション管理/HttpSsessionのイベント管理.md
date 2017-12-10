# HttpSessionのイベント管理

- HttpSesionのイベントオブジェクト

|発生するタイミング|イベントクラス名|
|---|---|
|生成・破棄|HttpSessionEvent|
|活性化・非活性化|HttpSessionEvent|
|属性への追加・変更・削除|HttpSessionBindingEvent|
|属性の登録・切り離し|HttpSessionBindingEvent|

- HttpSesionのリスナーインタフェース

|発生するタイミング|イベントクラス名|
|---|---|
|生成・破棄|HttpSessionListener|
|活性化・非活性化|HttpSessionActivationListener|
|属性への追加・変更・削除|HttpSessionAttributeListener|
|属性の登録・切り離し|HttpSessionBindingListener|

- HttpSessionListenerのリスナーインタフェースのメソッド

|メソッド名|説明|
|---|---|
|sessionCreated(HttpSessionEvent)|セッションが生成された直後に呼ばれるメソッド|
|sessionDestroyed(HttpSessionEvent)|セッションが破棄される直前に呼ばれるメソッド|

- HttpSessionAttributeListenerのリスナーインタフェースのメソッド

|メソッド名|説明|
|---|---|
|attributeAdded(HttpSessionBindingEvent)|オブジェクトに属性が追加された直後に呼び出されるメソッド|
|attributeRemoved(HttpSessionBindingEvent)|オブジェクトから属性が削除された直後に呼び出されるメソッド|
|attributeReplaced(HttpSessionBindingEvent)|オブジェクトに保持されている属性が変更された直後に呼び出されるメソッド|

リスナークラスはWebコンテナによってインスタンス化されるためweb.xmlに登録する必要がある。
```xml
<web-app>
    <listener>
        <listener-class>リスナークラス名（完全修飾）</listener-class>
    </listener>
</web-app>
```

## HttpSessionActivationListenerとHttpSessionBindingListener

- 非活性化
    - クライアントから一定時間アクセスが無いとファイルやDBなどの永続ストレージに退避させることがある
- 活性化
     - クライアントからアクセスがあった場合、永続ストレージからメモリ上に展開させる

- HttpSessionActivationListenerのインタフェースメソッド

|メソッド名|説明|
|---|---|
|sessionWillPassivate(HttpSessionEvent)|セッションオブジェクトが非活性化する前に呼ばれるメソッド|
|sessionDidActivate(HttpSessionEvent)|セッションオブジェクトが活性化した直後に呼び出されるメソッド|

- HttpSessionBindingListenerのインタフェースメソッド

|メソッド名|説明|
|---|---|
|valueBound(HttpSessionBindingEvent)|セッションオブジェクトに自身がセットされるときに呼ばれるメソッド|
|valueUnbound(HttpSessionBindingEvent)|セッションオブジェクトに自身が削除されるときに呼び出されるメソッド|

- HttpSessionActivationListenerとHttpSessionBindingListenerはweb.xml登録は不要
    - HttpSessionオブジェクトを監視することで呼び出しが可能なため