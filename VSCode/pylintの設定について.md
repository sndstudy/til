# pylintの設定について

`ファイル＞基本設定＞設定`から変更する

- 設定変更前
    - `"python.linting.pylintUseMinimalCheckers": true`
- 設定変更後
    - `"python.linting.pylintUseMinimalCheckers": false`
    - `false`にすることでpylintの警告を強くすることができる
    - 例えばdocstringが無いことも警告してくれるようになる