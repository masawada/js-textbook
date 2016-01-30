# DOM
DOMとはDocument Object Modelの略です。JavaScriptからHTMLの文章を操作するときはDOMという形式で操作をします。

## HTMLとDOM
JavaScriptからHTMLを操作するときに、JavaScriptでいちいちHTMLのタグを解釈するコードを書くより、始めからJavaScriptのオブジェクトとして扱える様になっていたほうが当然便利です。

そのための関数やプロパティのことをDOMと呼びます。

### windowオブジェクト
ブラウザ上でのグローバルオブジェクトは`window`というオブジェクトです。
ブラウザ上で変数や関数を宣言すると、windowオブジェクトの下に作られます。

```html
<script>
var hoge = 'hoge';

console.log(window.hoge === hoge);
// 上はtrueになる
</script>
```

## JavaScriptからDOMを扱う

始めに、JavaScriptからDOMのタグ、要素、ノードを取得する方法を紹介します。

### getElementById
指定したidを持つ要素のオブジェクトを返す。

```js
// <button id="button">送信</button> に対して
var button = document.getElementById('button');
```

### getElementsByClassName
指定したclass名を持つ要素のリストを返す。ここで返ってくるリストはArrayオブジェクトではなくNodeListオブジェクトであるので注意。

```js
// <button class="button">ボタン1</button>
// <button class="button">ボタン2</button>
// <button class="button">ボタン3</button>
// この3つのオブジェクトが格納されたNodeListオブジェクトが返ってくる
var buttonList = document.getElementsByClassName('button');
```

### getElementsByTagName
指定したタグ名を持つノードのリストを返す。ここで返ってくるリストもNodeListオブジェクトなので注意。

```js
// <button>ボタン1</button>
// <button>ボタン2</button>
// <button>ボタン3</button>
// この3つのオブジェクトが格納されたNodeListオブジェクトが返ってくる
var buttonList = document.getElementsByTagName('button');
```

### getElementsByName
指定したname属性を持つ要素のリストを返す。ここで返ってくるリストはHTMLCollectionなので注意。

```js
// <button name="button">ボタン1</button>
// <button name="button">ボタン2</button>
// <button name="button">ボタン3</button>
// この3つのオブジェクトが格納されたHTMLCollectionオブジェクトが返ってくる
var buttonList = document.getElementsByName('button');
```

### querySelector

```js
// getElementById('button')とした時と同じ
var button = document.querySelector("#button");

// クラス名がbuttonClassである要素の文書中で一番最初の要素を返す
var div = document.querySelector(".buttonClass");
```

### querySelectorAll

```js
// クラス名がbuttonClassである要素のNodeListを返す。
var buttons = document.querySelectorAll('.buttonClass');
```

-

次に、要素の中身(テキストなど)の扱い方について紹介します。

### innerHTML
`innerHTML`プロパティは、その要素の中にあるHTML文書の内容を取得します。

```html
<script>
var main = document.getElementById('main');
console.log(main.innerHTML);
// <p>Main Page</p>と表示される
</script>

<div id="main">
  <p>Main Page</p>
</div>
```

また`innerHTML`から、要素の内容を書き換えることが出来ます。

```js
main.innerHTML = '<h1>Main Page!!!</h1>'

// <div id="main">
//   <h1>Main Page!!!</h1>
// </div>
// にHTMLが書き換わる
```

### textContent
`textContent`プロパティは、その要素の中にあるテキストの内容を取得します。

```html
<div id="main">
  <p>Main Page</p>
</div>

<script>
var main = document.getElementById('main');
console.log(main.textContent);
// 'Main Page'と表示される
</script>
```

`textContent`も同様に、要素のテキストの内容を書き換えることが出来ます。

```js
main.textContent = 'Main Page!!!!'

// <div id="main">
//   <p>Main Page!!!!</p>
// </div>
// にpタグのテキストが書き換わる
```

#### innerHTMLとtextContentの違い
見て分かる通り`innerHTML`と`textContent`には大きな違いがあって、それは要素の中のHTML文書を取得するか、テキストのみを取得するかの違いです。

要素内のテキストのみを書き換えるのに`innerHTML`を用いると、余分なもの(タグの情報等)まで取得してしまうので、`textContent`の方が向いています。

逆に、要素内にあたらしいタグを追加するのに`textContent`を用いてしまうと、タグが解釈されずにそのまま表示されてしまいます。

このように似たようなことができるプロパティですが、必要な場面によって使い分ける必要があります。