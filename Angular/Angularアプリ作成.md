# Angularアプリ作成

AngularCLIを用いたAngularアプリの作成手順を記載する。

## 前提条件

- Node.js
    - v.8.11.3
- npm
    - v.5.6.0

## プロジェクト作成手順

1. AngularCLIをインストールする

- `npm install -g @angular/cli`
    - 最新のAngularCLIがインストールされる

2. 以下のコマンドを実行してAngularプロジェクトを作成する

- `ng new <プロジェクト名>`
    - 例）`ng new HogeProject`

3. 作成されたプロジェクトに移動する

- `cd <プロジェクト名>`

4. 以下のコマンドを実行してサンプルアプリが起動することを確認する

- `ng serve`
    - 起動後 **http://localhost:4200/** にアクセスすることで確認できる

## IEでアプリの起動を確認する場合

- srcフォルダに格納されている **polyfills.ts** の以下の箇所をコメントアウトして、再度起動してください

```ts
/** IE9, IE10 and IE11 requires all of the following polyfills. **/
// import 'core-js/es6/symbol';
// import 'core-js/es6/object';
// import 'core-js/es6/function';
// import 'core-js/es6/parse-int';
// import 'core-js/es6/parse-float';
// import 'core-js/es6/number';
// import 'core-js/es6/math';
// import 'core-js/es6/string';
// import 'core-js/es6/date';
// import 'core-js/es6/array';
// import 'core-js/es6/regexp';
// import 'core-js/es6/map';
// import 'core-js/es6/weak-map';
// import 'core-js/es6/set';
```

## 参考サイト

- Angular CLI
    - https://cli.angular.io/