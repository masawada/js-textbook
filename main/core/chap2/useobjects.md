# 組み込みオブジェクトの使用
JavaScriptにはあらかじめ幾つかのオブジェクトが用意されています。代表的なものを幾つか紹介します。

* Array
* Object
* Date
* Number
* String
* Math

## Array
Arrayは配列を扱うオブジェクトです。Arrayオブジェクトは次のように使います。
```
var array = new Array(1, 2, 3);

console.log(array);  // [1, 2, 3]
```
他に次のような書き方をしても配列を使うことが出来ます。
```
var array = [1, 2, 3, 4];

console.log(array);  // [1, 2, 3, 4]
```
今までやってきた書き方は下の`var array = [1, 2, 3, 4]`のような書き方です。これは内部的には`new Array(1, 2, 3, 4)`と同じことをしているのですが、簡素な書き方が好まれることが多いため`[1, 2, 3, 4]`の方を用います。

Arrayオブジェクトでよく使うメソッドやプロパティです。

プロパティ
 * `length`

メソッド
 * `join`

次の3つはfor文の代わりになるので、なるべく覚えておきたいメソッドです。繰り返しの処理をさせるときは、できるだけfor文を用いないでこれらのメソッドを用いたほうが、処理を簡潔に書くことが出来ます。
 * `forEach`
 * `map`
 * `filter`

`forEach`の例(`['a', 'b', 'c', 'd']`を列挙します)
```
var a = ['a', 'b', 'c', 'd'];

a.forEach(function(item) {
  console.log(item);
});
```

`map`の例(`[1, 2, 3, 4, 5]`のそれぞれの要素を2乗した配列を返します)
```
var a = [1, 2, 3, 4, 5];

var result = a.map(function(item) {
  return Math.pow(item, 2);
});

console.log(result);

// [ 1, 4, 9, 16, 25 ]
```

`filter`の例(`filter`では配列の数値が10以上のものの配列を返します)
    ```
var a = [1, 2, 3, 4, 5];

var result = a.map(function(item) {
  return Math.pow(item, 2);
});

var result2 = result.filter(function(item) {
  return item > 10;
});

console.log(result2);
// [ 16, 25 ]
```

## Object
次項に後述します。

## Date
Dateは日付や時刻を扱うオブジェクトです。Dateオブジェクトは以下のようにして使います。
```
var d = new Date();

console.log(d);
// Sat May 23 2015 15:58:44 GMT+0900 (JST)
```

この`Sat May 23 2015 15:58:44 GMT+0900 (JST)`というものは文字列ではなく、Dateオブジェクトの値であることに注意してください。

Dateオブジェクトでよく用いられるメソッドです。
 * `toString`
 * `getDate`
 * `getMonth`

最後の`getMonth`には注意が必要で、返ってくる結果は具体的な月の名前ではなく`0~11`までの数値です。次の例のように、月の名前が入っている配列に対して用いることが多いため、数値が返ってくるようになっています。
```
var month = ['Jan', 'Feb', 'Mar', 'Apr', 'May'][(new Date).getMonth()];

console.log(month);
// May
```

## Number
 * NaN

## String
Stringオブジェクトは少し注意の必要なオブジェクトです。次の例はGoogle Chromeで実行した結果です。

```
var str = new String('hello world!');

console.log(str);
// String {0: "h", 1: "e", 2: "l", 3: "l", 4: "o", 5: " ", 6: "w", 7: "o", 8: "r", 9: "l", 10: "d", 11: "!", length: 12, [[PrimitiveValue]]: "hello world!"}
```

`console.log(str)`で`str`のStringオブジェクトの中身を全て表示していることになります。

今まで使ってきた書き方は次のようなものでした。
```
var str = 'hello world!';

console.log(str);
// hello world!
```

このようにプリミティブ値としての文字列の返り値と`new String()`したときの返り値は違うので注意が必要です。

また、前項の'高度な解説'で出てきた、`.length`の過程は次のようなことになっています。

上のコードは内部では以下のようになっている。
```
var str = 'hello world!';
str.length;  // 12
```

```
var str = 'hello world!';
new String(str).length; // 12
```

Stringオブジェクトでは以下のようなメソッドがよく用いられます。
 * `split`
 * `slice`
 * `indexOf`

## Math
Mathオブジェクトは数学的な定数(円周率や自然対数など)と関数を提供するプロパティとメソッドを持つオブジェクトです。Mathオブジェクトは少し特殊で、インスタンスを生成する必要がない静的メソッド（クラスメソッド）です。

Mathオブジェクトでよく用いるメソッドやプロパティです。

プロパティ
 * `PI`
 * `E`

メソッド
 * `pow`
 * `sqrt`
 * `random`
