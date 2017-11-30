# WEB-INFの中身

- WEB-INF/classes
    - サーブレットやJavaクラスなどのクラスファイルを格納する。パッケージ化したクラスはパッケージに対応したディレクトリに格納する。
- WEB-INF/lib
    - JARファイルを格納する。ここに格納されたファイルはWebコンテナ起動時にクラスパスが設定される。
- WEB-INF/web.xml
    - Webアプリケーションの設定ファイル
- WEB-INF/tags(JARファイルの場合はMETA-INF/tags)
    - カスタムタグに関するタグファイルである*.tag *.tagxを格納する
- WEB-INF/*.tld(JARファイルの場合はMETA-INF/*.tld)
    - カスタムタグを使用する際に必要となる設定ファイル
