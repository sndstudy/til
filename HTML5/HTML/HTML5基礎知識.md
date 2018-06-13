# HTML5基礎知識

## 基本的な書式と各部の名称

- 文書内の各構成要素を **要素(Element)** という
- 要素の前につけるタグを **開始タグ**
- 要素の後につけるタグを **終了タグ**

```html
<h1>←開始タグ 終了タグ→</h1>
```

- 開始タグが省略できる要素(条件による)
    - html
    - head
    - body
    - colgroup
    - tbody

- 要素を開始タグだけで示すものがある。そのような要素を **空要素** という
- 空要素には終了タグを指定できない
- 空要素の例
    - img
    - br
    - input
    - meta
    - link
- 空要素のタグの`>`の直前には`/`を入れることができる
```html
<br>
<br />
```

## HTMLの全体構造

- HTML文書の先頭内容には **DOCTYPE宣言**を配置する
- DOCTYPE宣言の後に`<html>` `<head>` `<body>`を配置する
```html
<!DOCTYPE html>
<html>
    <head>
    </head>
    <body>
    </body>
</html>
```

## DOCTYPE宣言

- 大文字、小文字どちらで記載してもOK
```html
<!DOCTYPE html>
<!DOCTYPE HTML>
<!doctype html>
<!-- どれもOK -->
```

## 文字参照

- HTML上で特別な役割を持つを文字をそのまま表示したい場合は **文字参照** という書式で書く

|表示させたい文字|文字参照|
|---|---|
|<|\&lt;|
|>|\&gt;|
|&|\&amp;|
|&copy;|\&copy;|
|&reg;|\&reg;|

