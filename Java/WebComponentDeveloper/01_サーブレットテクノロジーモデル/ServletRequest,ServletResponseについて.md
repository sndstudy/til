# ServletRequest,ServletResponseについて

## ServletRequestインタフェースのメソッド
|メソッド名|説明|
|---|---|
|int getContentLength()|リクエストのボディ、入力ストリームから読み込めるバイト数を返却|
|String getContentType()|メッセージボディのMIMEタイプを返却|
|ServletInputStream getInputStream()|データを読み込むためのStreamを返却|
|BufferedReader getReader()|データを読み込むためのReaderを返却|
|String getRemoteAddr()|リクエストを送ったクライアントまたは最後のプロキシの送信元IPを返却|
|String getRemoteHost()|リクエストを送ったクライアントまたは最後のプロキシの送信元ドメイン名を返却|
|int getRemotePort()|リクエストを送ったクライアントまたは最後のプロキシの送信元IPポートを返却|
|String getServerName()|要求を受信したサーバのホスト名を返却|
|int getServerPort()|要求を受信したサーバのポート番号を返却|

## HttpServletRequestインタフェースのメソッド
|メソッド名|説明|
|---|---|
|Cookie[] getCookies()|送られてきたすべてのCookieオブジェクトを返却|
|String getHeader(String)|指定したリクエストヘッダーの値を返却|
|Enumeration getHeaders(String)|指定いたリクエストヘッダーのすべての値を返却|
|Enumeration getNames()|リクエストに含まれるすべてのヘッダー名を返却|
|int getIntHeader(String)|指定したリクエストヘッダーの値を返却|

## ServletResponseインタフェースのメソッド
|メソッド名|説明|
|---|---|
|void setContentType(String)|コンテントタイプを設定する|
|ServletOutputStream getOutputStream()|バイナリデータを出力するために使用するStreamオブジェクトを取得する|
|PrintWriter getWriter()|文字データを出力するために使用するWriterオブジェクトを取得する|

## HttpServletResponseインタフェースのメソッド
|メソッド名|説明|
|---|---|
|void addCookie(Cookie)|Cookieをレスポンスに追加する|
|void addHeader(String name, String value)|指定された名前で指定された値を持つレスポンスヘッダーを追加|
|void setHeader(String name, String value)|指定された名前で指定された値を持つレスポンスヘッダーを設定。既に設定されている場合は上書き。|

## Cookieの利用
- Cookieオブジェクトの作成
    - `Cookie cookie = new Cookie(name, value)`

|メソッド名|説明|
|---|---|
|void setSecure(boolean)|HTTPSのようなセキュアなプロトコルを使用している場合のみCookieを送り返すようにブラウザに指示する|
|void setMaxAge(int)|Cookieの最長存続期間を秒単位で設定|
|String getName()|名前を返す|
|String getValue()|値を返す|