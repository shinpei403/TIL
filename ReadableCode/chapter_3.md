# Chapter_3メモ

最善の名前とは誤解されない名前のこと。<br>
[filter, length, limit]のように意味があいまいな単語は避ける。

## 例

 * filter
 
filterが「選択する」なのか「除外する」なのかあいまい。<br>

「選択する」→[select] <br>
「除外する」→[exclude]

 * Clip(text, length) 段落の内容を切り抜く関数

Clip()の動作は二つ考えられる

 最後からlength文字を削除する(remove)<br>
 最大length文字まで切り詰める(truncate)<br>

 後者に可能性が高いが、確実性がない。後者の場合は[Truncate(text, length)]に変えた方がいい。<br>
 また[length]も[max_length]にしたほうが明確になる。<br>
 これで終わりではなく、[max_length]も色々な解釈ができる<br>
 「バイト数、文字数、単語数」など。<br>
 文字数の場合は[max_length→max_chars]に変更するといい。

 * 限界値を含める時はminとmaxを使う
```
CART_TOO_BIG_LIMIT = 10

if shopping_cart.num_items() >= CART_TOO_BIG_LIMIT:
  Error('カートにある商品数が多すぎます。')
```

上記のままだと名前があいまいになる。<br>
この名前だと「未満(限界値をふくまない)なのか、以下(限界値を含む)なのかが分からない。<br>
下記のようにすればいい。
```
MAX_ITEMS_IN_CART = 10

if shopping_cart.num_items() > CART_TOO_BIG_LIMIT:
  Error('カートにある商品数が多すぎます。')
```

 * 包含的範囲を指定するときはfirstとlastを使う
```
#start,stopの例
print integer_range(start=2, stop=4)
#これの範囲は[2, 3]なのか、[2, 3, 4]なのかが曖昧。

#包含的(終端を含む)な範囲を表すのであれば、firstとlastを使うのがいい。

set.PrintKeys(first='Bart', last='Maggie')
```

 * 排他的範囲(終端を含めない)

```
#PrintEventsInRange(begin, end)
#使用例 10月16日に開催されたイベントを全て印字する
PrintEventsInRange('OCT 16 12:00am', 'OCT 17 12:00am')
```

* ブール値(真偽)の名前

ブール値の変数やブール値を返す関数の名前を選ぶときには、trueとfalseの意味を明確にしなければならない。

```
bool read_password = true

#上記の場合は2つの意味に解釈できる
#パスワードをこれから読み取る必要がある
#パスワードを既に読み取っている。
#下記に変更した方がいい。

need_password
user_is_authenticated

#ブール値の変数名にはis, has, can, shouldなどをつけてわかりやすくすることが多い。

SpaceLeft() 
#数値を返すように聞こえるので、下記に修正する
HasSpaceLeft()

#また名前を否定形にするのは避ける

bool disable_ssl = false

#下記の肯定形に修正する

bool use_ssl = true
```
* 単語に対するユーザーの期待に注意する

get()やsize()は軽量なメソッドが期待されているので、計算量の多いメソッドの名前には使わない。


