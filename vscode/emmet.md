# VScodeでの Emmet

## htmlタグ展開
- `html:5` + Tabで実行 (`!`のみでのOK)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```
`lang="en"`を毎回`lang=ja`に変えるのは面倒なので以下の設定をすると良き

```json
"emmet.variables": {"lang" : "ja"},
```

## 通常のタグ
`h1` + Tagなど、タグ名入力してTabキーを押すと入力できる  
`img`も`<img src="" alt="">`と展開される

## classやidをつけて展開
- `h1#logo`＋Tabキーで`<h1 id="logo"></h1>`と展開されます。  
- タグを何も指定せずにclass,idだけで展開すると自動で`div`タグになる  
`.wrapper＋Tabキー`で`<div class="wrapper"></div>`

## 入れ子にする
`header>nev`のように`>`で繋ぐとネストできる
```html
<header>
    <nev></nev>
</header>
```
## テキストの挿入
`h1{Hello Emmet!}`という風に{}でテキストを囲って展開すると  
`<h1>Hello Emmet!</h1>`のような形で展開されます。

## 繰り返しの展開
`ul>li*3`のように`*N`でNの部分に数字を入れると、繰り返しで展開されます。

## 連番での展開
`ul>li#hoge$*3`のように連番させたいidやclassに`$`を付けると、その部分が連番になります。
```html
<ul>
    <li id="hoge1"></li>
    <li id="hoge2"></li>
    <li id="hoge3"></li>
</ul>
```

## ダミーテキスト
`lorem`＋Tabキーで
```html
Lorem ipsum dolor sit amet consectetur adipisicing elit. Libero veritatis odio magnam vel aut quaerat saepe eius repellendus, quisquam cupiditate inventore incidunt id eveniet, ex temporibus tempora dolore aspernatur sed?
```