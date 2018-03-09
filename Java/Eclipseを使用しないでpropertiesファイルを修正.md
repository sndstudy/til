# Eclipseを使用しないでpropertiesファイルを修正

JDKに含まれる`native2ascii`を使用する。
propertiesファイルの文字コードは**ISO 8859-1**のためテキストエディタで開くと文字化けした感じで表示される。

- テキストエディタで見れるようにする
    - `native2ascii -reverse [対象のpropertiesファイル名] [変換後のテキストファイル名]`

- 編集後、propertiesファイルに戻す場合
    - `native2ascii [変換前のテキストファイル名] [変換後のpropertiesファイル名]`

## 参考サイト

- https://nj-clucker.com/edit-properties-file-without-eclipse/