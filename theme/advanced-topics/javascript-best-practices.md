<!-- 
# JavaScript Best Practices
 -->

# JavaScript のベスト・プラクティス

<!-- 
Many themes use JavaScript to provide interactivity, animation or other enhancements. These best practices will help ensure your code works efficiently and does not cause conflicts with your content or plugins.
 -->

多くのテーマでは、インタラクティブ性やアニメーション、その他の機能強化のために JavaScript を使用しています。これらのベスト・プラクティスにより、あなたのコードが効率的に動作するようにし、あなたのコンテンツやプラグインとの競合を引き起こさないようにできます。

<!-- 
## Use Included Libraries
 -->

## 付属ライブラリの使用

<!-- 
There are many useful JavaScript libraries you may want to include when building your theme. Did you know that WordPress comes bundled with dozens of popular libraries? Check out this [list of default scripts included with WordPress](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress).
 -->

あなたのテーマを構築する際にインクルードしたい便利な JavaScript ライブラリは、数多く存在します。WordPress には数十もの人気ライブラリがバンドルされていることを知ってました ? この [WordPress にインクルードされている、デフォルト・スクリプトのリスト](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress) をご覧ください。

<!-- 
A common mistake made by beginning theme and plugin developers is to bundle their theme or plugin with their own version of the library. This may conflict with other plugins that enqueue the version bundled with WordPress. As a best practice, make your theme compatible with the version of your favorite library included with WordPress.
 -->

テーマやプラグインの開発を始めたばかりの人がよく犯す間違いは、テーマやプラグインに独自のバージョンのライブラリをバンドルすることです。これは、WordPress バンドル版をキューに追加する、他のプラグインと競合する可能性があります。ベスト・プラクティスとして、お気に入りのライブラリの WordPress バンドル版と互換性のある、あなたのテーマを作りましょう。

<!-- 
Do not try to use your own version of a JavaScript library that is already [bundled](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress "Default Scripts Included with WordPress") with WordPress. Doing so may break core functionality and conflict with plugins.
 -->

WordPress にすでに [バンドル](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress "WordPress にインクルードされている、デフォルト・スクリプト") されている JavaScript ライブラリの独自版を、使用しようとしないでください。そのようなことをすると、コア機能が破損したり、プラグインと競合したりする可能性があります。

<!-- 
If you feel you MUST replace the WordPress version with one of your own… well… the answer is still: don’t do it.  The versions of JavaScript libraries used by WordPress may include custom tweaks that WordPress needs to operate.  Any time you override these libraries, you risk breaking your WordPress instance. Moreover, plugins created by other authors should be written to be compatible with WordPress’s version of these libraries as well. Adding your own version may (and often does!) conflict with plugins.
 -->

WordPress 版を、どうしても自分で用意したものと置き換えたいと思うなら…ええと… 答えは、変わりません: やめておけ。WordPress で使用される JavaScript ライブラリのバージョンには、WordPress の動作に必要なカスタム調整が含まれている場合があります。これらのライブラリをオーバーライドすると、WordPress インスタンスが破損するリスクがあります。さらに、他の作者が作成したプラグインも、WordPress が提供するこれらのライブラリのバージョンと互換性があるように、記述する必要があります。独自のバージョンを追加すると、プラグインと競合する可能性があります (そして実際によくある !)。

<!-- 
## Standard JavaScript
 -->

## 標準 JavaScript

<!-- 
Javascript is growing in popularity for web developers, and it’s being used to accomplish for a variety of tasks. Here are some best practices to use when writing your JavaScript
 -->

JavaScript は Web 開発者にとって人気が高まっており、さまざまなタスクを達成するために使用されています。あなたの JavaScript を記述する際に活用できる、ベスト・プラクティスをいくつか

<!-- 
*   Avoid Global Variables
*   Keep your JavaScript unobtrusive
*   Use closures and the [module pattern](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules)
*   Stick to a coding style. Use The [WordPress Javascript Coding Standard](https://make.wordpress.org/core/handbook/coding-standards/javascript/).
*   Validate and Lint Your Code – [E](http://JSLint.com)[S](http://JSLint.com)[Lint.com](https://eslint.org/)
*   Ensure your site still works without JavaScript first – then add JavaScript to provide additional capabilities. This is a form of [Progressive Enhancement](http://en.wikipedia.org/wiki/Progressive_enhancement).
*   Lazy load assets that aren’t immediately required.
*   Don’t use jQuery *if you don’t need to* — There’s a great site that shows you how to do some common tasks with plain old JavaScript – [you might not need jQuery](http://youmightnotneedjquery.com)
 -->

*   グローバル変数は、避けましょう
*   あなたの JavaScript を、非侵襲的に維持しましょう
*   クロージャと [モジュール・パターン](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) を利用しましょう
*   コーディング・スタイルを統一しましょう。[WordPress Javascript コーディング標準](https://make.wordpress.org/core/handbook/coding-standards/javascript/) を使用しましょう。
*   あなたのコードを検証し、リントしましょう – [E](http://JSLint.com)[S](http://JSLint.com)[Lint.com](https://eslint.org/)
*   まず、JavaScript 不使用で、あなたのサイトが正常に動作することを確認しましょう – 次に、追加機能を提供するために JavaScript を追加しましょう。これは [プログレッシブ・エンハンスメント (漸進的拡張)](http://en.wikipedia.org/wiki/Progressive_enhancement) の一形態です。
*   すぐに必要とされないアセットは、遅延ロードしましょう。
*   *必要ないなら* jQuery を使用しないでください — 普通の古い JavaScript で、よくあるタスクを実行する方法を教えてくれる、すばらしいサイトがあります – [jQuery は、必要ないかもしれません](http://youmightnotneedjquery.com)

## jQuery

<!-- 
### Including jQuery in your theme
 -->

### あなたのテーマへの jQuery のインクルード

<!-- 
[jQuery](http://www.jquery.com) is a popular JavaScript library to make working with JavaScript easier and more reliable across browsers. If you use jQuery, be sure to [follow the handbook guidelines on including JavaScript](https://developer.wordpress.org/themes/basics/including-css-javascript/). Giving your theme’s enqueued .js files a dependency array of `array( 'jquery' )` ensures that the jQuery script has been downloaded and loaded before your theme’s code.
 -->

[jQuery](http://www.jquery.com) は、ブラウザ間で JavaScript の操作をより簡単かつ信頼性の高いものにする、人気の JavaScript ライブラリです。jQuery を使用する場合は、必ず [JavaScript のインクルードについては、ハンドブックのガイドラインに準拠](https://developer.wordpress.org/themes/basics/including-css-javascript/) を行ってください。あなたのテーマのエンキューされた `.js` ファイルに `array( 'jquery' )` の依存関係の配列を指定することで、jQuery スクリプトがあなたのテーマのコードよりも先にダウンロードされ、ロードされることを保証します。

<!-- 
#### Using $
 -->

#### `$` の使用

<!-- 
Because the copy of jQuery included in WordPress loads in `[noConflict()](https://api.jquery.com/jQuery.noConflict/)` mode, use this wrapper code in your theme’s .js files to map “$” to “jQuery”:
 -->

WordPress にインクルードされている jQuery のコピーは `[noConflict()](https://api.jquery.com/jQuery.noConflict/)` モードでロードされるため、あなたのテーマの `.js` ファイルで、このラッパーコードを使用して「$」を「jQuery」にマッピングしましょう:

```javascript
( function( $ ) {
// Your code goes here
} )( jQuery );
```

<!-- 
This wrapper (called an Immediately Invoked Function Expression, or IIFE) lets you pass in a variable—jQuery—on the bottom line, and give it the name “$” internally. Within this wrapper you may use `$` to select elements as normal.
 -->

このラッパー (即時実行関数式、または IIFE と呼ばれる) は、最下行で変数 — jQuery — を渡すことを可能にし、内部でこれに「$」という名称を付けます。このラッパー内では、通常通り `$` を使用して要素を選択できます。

<!-- 
### Selectors
 -->

### セレクタ

<!-- 
Every time you select an element with jQuery, it performs a query through your document’s markup. These queries are very fast, but they do take time—you can make your site respond faster by re-using your jQuery objects instead of using a new query. So instead of repeating selectors:
 -->

jQuery で要素を選択するたびに、あなたのドキュメントのマークアップを通じて、クエリーを実行します。これらのクエリーは非常に高速ですが、それでも時間を要します — 新規クエリーを使用する代わりにあなたの jQuery オブジェクトを再利用することで、あなたのサイトの応答速度を向上させることができます。したがって、セレクタを繰り返す代わりに:

```javascript
// Anti-pattern
$('.post img').addClass('theme-image');
$('.post img').on('click', function() { ... });
```

<!-- 
it is recommended to **cache your selectors** so you can re-use the returned element without having to repeat the lookup process:
 -->

返された要素を再利用する際、検索プロセスを繰り返す必要がないようにするため、**あなたのセレクタをキャッシュする** ことをおすすめします:

```javascript
var $postImage = $('.post img');
// All image tags within posts can now be accessed through $postImage
$postImage.addClass('theme-image');
$postImage.on('click', function() { ... });
```

<!-- 
### Event Handling
 -->

### イベント処理

<!-- 
When you use jQuery methods like `.bind` or `.click`, jQuery creates a new browser event object to handle processing the requested event. Each new event created takes a small amount of memory, but the amount of memory required goes up the more events you bind. If you have a page with a hundred anchor tags and wanted to fire a \`logClick\` event handler whenever a user clicked a link, it is very easy to write code like this:
 -->

`.bind` や `.click` のような jQuery メソッドを使用する際、jQuery は、要求されたイベントの処理を扱うために新規のブラウザ・イベント・オブジェクトを作成します。作成される新規イベントごとに少量のメモリが消費されますが、バインドするイベントが増えるほど必要なメモリ量は増加します。ページに100個のアンカー・タグがあり、ユーザーがリンクをクリックするたびに `logClick` イベント・ハンドラを起動したい場合、次のようなコードを書くのは非常に簡単です:

```javascript
// Anti-pattern
$('a').click( logClick );
```

<!-- 
This works, but under the hood you have asked jQuery to create a new event handler for every link on your page.
 -->

これは機能しますが、内部的には、あなたのページ上のすべてのリンクに対して新規のイベントハンドラを作成するよう jQuery に指示しています。

<!-- 
**Event delegation** is a way to accomplish the same effect with less overhead. Because events in jQuery “bubble”—that is, a click event will fire on a link, then on the link’s surrounding `<p>` tag, then on the `div` container, and so on up to the `document` object itself—we can put a single event handler higher up in the page structure, and still catch the click events for all of those links:
 -->

**イベント委譲** は、より少ないオーバーヘッドで同じ効果を達成する方法です。jQuery でのイベントは「バブルアップ」する — つまり、クリック・イベントは、リンク上で発生し、次にリンクを囲む `<p>` タグ上で、`div` コンテナ上で発生し、このようにして `document` オブジェクト自体に至るまで発生する — ため、ページ構造の上位で一つのイベント・ハンドラを配置しても、それらのリンクすべてに対するクリック・イベントを捕捉できます:

```javascript
// Bind one handler at the document level, which is triggered
// whenever there is a "click" event originating from an "a" tag
$(document).on('click', 'a', logClick);
```