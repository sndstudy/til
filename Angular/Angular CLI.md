# Angular CLI

## 新規プロジェクトの作成

- `ng new [プロジェクト名]`

## サーバー起動

- `ng serve`

## コンポーネント作成

- `ng generate component [コンポーネント名]`
    - コンポーネントの雛型が作成される
    - `app.module.ts`の`declarations`に追記される

## サーバーを起動せずに動作確認したい場合

1. `ng build`でビルドを行う
1. `ng build`で生成された`index.html`を開いて動作確認をする

### 注意事項

サーバーを起動せずに動作確認をした場合、JSやCSSファイルが見つからないエラーが発生する場合がある。

その場合は`ng build --bh ./`でビルドを実行する。

`--bh`はベースのディレクトリを設定する。`./`は同じディレクトリ内のJS、CSSファイルを参照するようになる。

デフォルトは`/`のため、ルートディレクトリになる。

## 参考サイト

- https://cli.angular.io/
    - Angular CLI 公式
- https://github.com/angular/angular-cli/wiki/build
    - buildについて