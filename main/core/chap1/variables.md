# 変数と型
## 型
JavaScriptには以下の値の型があります。

* Number (数値)
* String (文字列)
* Boolean (論理値)
* Null
* Undefined
* Object

### Number
数値を表す型はNumber型ただ1つのみであり、内部的には64bitの浮動小数です。これはC言語で言えばdoubleと等しく、JavaScriptにはdouble型のみが存在するとも考えられます。

数値は数字列で表現します。通常は10進数で解釈されますが`0x`で始まる数字列は16進数の数値として解釈されます。

##### Number型の値の例:
```js
1
3.0
0xFF
```

### String
文字列を表すのがString型です。文字を表す型は存在しません。

文字列はシングルクオート(`'`)またはダブルクオート(`"`)で0個以上の文字を囲うことで表現します。文字列には日本語を含むこともできます。

##### String型の値の例:
```js
'abcdefg'
"いろはにほへとちりぬるを"
```

### Boolean
論理値を表すのがBoolean型です。論理値のことを真偽値とも言います。Boolean型は`true`と`false`2つの値しか持ちません。

##### String型の値の例:
```js
true
false
```

### Null
Null型はただ1つの値`null`のみを持ちます。`null`は有効な値が存在しないことを示すための値です。

##### Null型の値の例:
```js
null
```

### Undefined
Undefined型はNull型と同様にただ1つの値`undefined`のみを持ちます。役割も`null`に似ていますが`undefined`は変数が宣言されているが定義はされていない「未定義値」を表します(変数については次項で説明します)。

##### Null型の値の例:
```js
undefined
```

### Object
Object型はこれまで説明してきた型とは一味違った型です。これまで説明してきた型の値はプリミティブ値(プリミティブとは原始的な、単純なという意味)と呼び、最も基本的な値として扱います。一方Object型は関数や配列、辞書(仕様上、厳密には辞書は存在しませんが便宜上そう呼ぶことにします)などを表すための型です。

JavaScriptを理解することはすなわちこのObject型の性質を理解することと言っても良いほど奥が深い型です。そのためこの章での言及は避け、後の章で詳しく解説します。

## 変数
変数を宣言するには以下のように`var`というキーワードと識別子(名前)を用います。JavaScriptにおいて変数の宣言時に型を指定する必要はありません。識別子には数字、文字、`_`、`$`を用いることが出来ます。ただし変数名の先頭に数字を使うことはできません。また予約語を識別子として使うことはできません。(予約語については後述します)

セミコロン(`;`)を用いて文の終わりを示します。`var`を使わなくても変数を宣言できます。また`;`を省略できる場合があります。しかし意図しない動作の原因となることがあるため`var`と`;`はつけるようにしましょう。

```js
var [識別子] = [値];
```

##### 例:
```js
var message = 'hello, world';
```

## 予約語
以下の識別子は予約語であり変数名などに用いることはできません。

```
break do instanceof typeof
case else new var
catch finally return void
continue for switch while
debugger function this with
default if throw
delete in try
```

また以下の識別子は将来のための予約語として通常の予約後と同様に識別子として用いることが出来ません。

```
class enum extends super
const export import
```
