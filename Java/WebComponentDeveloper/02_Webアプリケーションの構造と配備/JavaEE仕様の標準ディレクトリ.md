# JavaEE仕様の標準ディレクトリ

### ディレクトリ構成
- WebApp
    - WEB-INF
        - classes
        - src
        - web.xml
- HTML,JSPファイルなど

### 説明
- WebApp（コンテキストルート）
    - このディレクトリ以下にWebアプリケーションを構成する際に必要なディレクトリ、ファイルを格納する
    - ディレクトリの名前は任意でOK
- WEB-INF
    - コンテキストルート直下に配置しなければならないディレクトリ
    - ディレクトリ名は「WEB-INF」で大文字半角である必要がある
- classes
    - Javaのクラスファイルを格納するディレクトリ
    - 配置はコンテキストルート\WEB-INF以下で名前は「classes」で小文字半角である必要がある
- web.xml
    - サーブレットとURLの紐づけやその他設定を行う
    - 配置はコンテキストルート\WEB-INF以下で名前は「web.xml」で小文字半角である必要がある
- src
    - 任意のフォルダ
    - ソースファイルを格納する
