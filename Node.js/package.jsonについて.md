# package.jsonについて

## scriptsの書き方

```
スクリプト名:コマンド
```

`npm run スクリプト名`でコマンドが実行される。スクリプト名は任意の名前でOK。

### 例:Webpackでbundle.jsを生成したいとき
```
"build":".\\node_modules\\.bin\\webpack .\\main.js bundle.js"
```

`npm run build`で実行される
