# JavaScript メモ

* コードを書く時はグローバルを汚染しないように、即時関数を使う  
 即時変数  
 ```
 (() => {
<!--  ここにコードを書く。   -->
 })();
 ```
* JavaScriptで変数名に$○○にすると明示的にDOM要素を表す。
* JavaScriptのIDはjs-○○にするとidを見た時に、すぐにJavaScriptで使われているとわかる。
* idやclassを使いたくない時はHTMLのdata属性を使うとよい。
```
 data-○○="0", data-○○="1"
```
* eventのdatasetプロパティはそのDOM要素のdata属性を取得する。<br><br>
```
<!--  html  -->
<a href="" class="tab-nav-item is-active" data-nav="0">Tab-0</a>
<!-- js -->
<!-- クリックされたnavとそのdataを取得 -->
const $this = e.target;
const targetVal = $this.dataset.nav; # 0が取得できる。
```
* 何回か出てきているものは変数や定数にして、メンテナンス性を高める。  

