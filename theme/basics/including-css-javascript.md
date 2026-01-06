<!-- 
# Including CSS &amp; JavaScript (Archived)
 -->

# CSS &amp; JavaScript のインクルード (アーカイブ済み)

<!-- 
This is an old page that has been archived in favor of the newer [Including Assets documentation](https://developer.wordpress.org/themes/core-concepts/including-assets/) in the Core Concepts chapter. This page will eventually be removed and redirect to the newer doc.
 -->

これは古いページであり、コアコンセプト章の新しい [アセット・ドキュメントのインクルード](https://developer.wordpress.org/themes/core-concepts/including-assets/) と入れ替わりにアーカイブされました。本ページは最終的に削除され、新しいドキュメントにリダイレクトされます。

<!-- 
When you’re creating your theme, you may want to create additional stylesheets or JavaScript files. However, remember that a WordPress website will not just have your theme active, it will also be using many different plugins. So that everything works harmoniously, it’s important that theme and plugins load scripts and stylesheets using the standard WordPress method. This will ensure the site remains efficient and that there are no incompatibility issues.
 -->

あなたのテーマを制作する際、追加のスタイルシートや JavaScript ファイルを制作したい場合もあるでしょう。ただし、WordPress サイトでは、あなたのテーマが有効化されるだけでなく、さまざまなプラグインも使用されることを覚えておいてください。すべてが調和して動作するためには、テーマとプラグインが、標準的な WordPress の方法でスクリプトやスタイルシートをロードすることが重要です。これによりサイトの効率性が保たれ、互換性の課題が発生しないことが保証されます。

<!-- 
Adding scripts and styles to WordPress is a fairly simple process.   Essentially, you will create a function that will enqueue all of your scripts and styles. When enqueuing a script or stylesheet, WordPress creates a handle and path to find your file and any dependencies it may have (like jQuery) and then you will use a hook that will insert your scripts and stylesheets.
 -->

WordPress にスクリプトやスタイルシートを追加する手順は、比較的簡単です。基本的には、あなたのスクリプトやスタイルシートのすべてを、エンキューする関数を作成します。スクリプトやスタイルシートをエンキューする際、WordPress はあなたのファイルと (jQuery などの) その依存関係を見つけるためのハンドルとパスを作成し、その後、フックを使用してあなたのスクリプトやスタイルシートを挿入します。

<!-- 
## Enqueuing Scripts and Styles
 -->

## スクリプトとスタイルのエンキューイング

<!-- 
The proper way to add scripts and styles to your theme is to enqueue them in the `functions.php` files. The `style.css` file is required in all themes, but it may be necessary to add other files to extend the functionality of your theme.
 -->

あなたのテーマにスクリプトやスタイルを追加する適切な方法とは、`functions.php` ファイルでそれらをエンキューすることです。`style.css` ファイルはすべてのテーマで必須ですが、あなたのテーマの機能を拡張するために、他のファイルを追加する必要があるかもしれません。

<!-- 
Tip: WordPress includes a number of JavaScript files as part of the software package, including commonly used libraries such as jQuery. Before adding your own JavaScript, [check to see if you can make use of an included library](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress).
 -->

ヒント: WordPress は、ソフトウェア・パッケージの一部として、jQuery などの一般的に使用されるライブラリを含む、多数の JavaScript ファイルを提供しています。独自の JavaScript を追加する前に、[付属のライブラリを利用できるかどうかチェック](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress) してください。

<!-- 
The basics are:
 -->

基本は、次の通りです:

<!-- 
1.  Enqueue the script or style using `wp_enqueue_script()`, `wp_enqueue_style()`, or `wp_enqueue_block_style`.
 -->

1.  `wp_enqueue_script()`、`wp_enqueue_style()`、または `wp_enqueue_block_style` を使用して、スクリプトまたはスタイルをエンキューします。

<!-- 
### Stylesheets
 -->

### スタイルシート

<!-- 
Your CSS stylesheets are used to customize the presentation of your theme. A stylesheet is also the file where information about your theme is stored. For this reason, the `style.css` file is **required in every theme.**
 -->

あなたの CSS スタイルシートは、あなたのテーマの表現をカスタマイズするために使用されます。スタイルシートはまた、あなたのテーマに関する情報が保存されるファイルでもあります。このため、`style.css` ファイルは、**すべてのテーマで必須** です。

<!-- 
Rather then loading the stylesheet in your `header.php` file, you should load it in using `wp_enqueue_style`. In order to load your main stylesheet, you can enqueue it in `functions.php`
 -->

あなたの `header.php` ファイルでスタイルシートをロードするのではなく、`wp_enqueue_style` を使用してロードする必要があります。あなたのメイン・スタイルシートをロードするには、`functions.php` でそれをエンキューできます。

<!-- 
To enqueue `style.css`:
 -->

`style.css` をエンキューするには:

```php
wp_enqueue_style( 'style', get_stylesheet_uri() );
```

<!-- 
This will look for a stylesheet named “style” and load it.
 -->

これは「style」という名前のスタイルシートを探し、ロードします。

<!-- 
The basic function for enqueuing a style is:
 -->

スタイルをエンキューするための基本関数は、次のとおりです:

```php
wp_enqueue_style( $handle, $src, $deps, $ver, $media );
```

<!-- 
You can include these parameters:
 -->

以下のパラメータを含めることができます:

<!-- 
*   **$handle** is simply the name of the stylesheet.
*   **$src** is where it is located. The rest of the parameters are optional.
*   **$deps** refers to whether or not this stylesheet is dependent on another stylesheet. If this is set, this stylesheet will not be loaded unless its dependent stylesheet is loaded first.
*   **$ver** sets the version number.
*   **$media** can specify which type of media to load this stylesheet in, such as ‘all’, ‘screen’, ‘print’ or ‘handheld.’
 -->

*   **$handle** 単にスタイルシートの名称です。
*   **$src** 保存場所です。残りのパラメータは、省略可能です。
*   **$deps** このスタイルシートが、他のスタイルシートに依存しているかどうかを示します。設定されている場合、依存スタイルシートが先にロードされない限り、このスタイルシートはロードされません。
*   **$ver** バージョン番号を設定します。
*   **$media** このスタイルシートを、どの種類のメディアでロードするかを指定できます。たとえば「all」、「screen」、「print」、「handheld」などです。

<!-- 
So if you wanted to load a stylesheet named “slider.css” in a folder named “CSS” in you theme’s root directory, you would use:
 -->

したがって、あなたのテーマのルート・ディレクトリにある「CSS」という名称のフォルダー内に、「slider.css」という名称のスタイルシートをロードしたい場合、次のように記述します:

```php
wp_enqueue_style( 'slider', get_template_directory_uri() . '/css/slider.css', false, '1.1', 'all');
```

<!-- 
## Including CSS for block styles
 -->

## ブロック・スタイル用 CSS のインクルード

<!-- 
In addition to `wp_enqueue_style()`, you can use `wp_enqueue_block_style()` to enqueue styles for blocks. [wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) requires WordPress version 5.9 or later.
 -->

`wp_enqueue_style()` に加えて、ブロック用のスタイルをエンキューするには `wp_enqueue_block_style()` を使用できます。[wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) は WordPress v5.9以降が必要です。

<!-- 
A key part of creating block themes is performance. With, `wp_enqueue_block_style()`, the theme only loads the CSS for the selected block when the block is used on the page.
 -->

ブロック・テーマ制作における重要な要素は、パフォーマンスです。`wp_enqueue_block_style()` を使用すると、テーマはページ上でブロックが使用された際にのみ、選択されたブロックの CSS をロードします。

<!-- 
The additional style is loaded in the editor and the front, after the block style provided by WordPress and the Gutenberg plugin. You can use this method to add block styles that you can not add via `theme.json`. For example, media queries.
 -->

追加のスタイルは、WordPress および Gutenberg プラグインが提供するブロック・スタイルの後に、エディターとフロントエンドでロードされます。この方法を使用すると、`theme.json` 経由では追加できないブロック・スタイルを追加できます。たとえば、メディア・クエリーなどです。

<!-- 
This code example changes the size and text color of the date in the latest comments block. Because this is a `time` HTML element that is nested inside other HTML elements, can not be styled using `theme.json`.
 -->

本コード例は、最新コメント・ブロック内の日付のサイズと文字色を変更します。これは他の HTML 要素内にネストされた `time` 要素であるため、`theme.json` を使用して、スタイルを設定できません。

<!-- 
First, create a new CSS file with the name of the block: `latest-comments.css`.  
Where you place the file depends on how you organize your theme files. In the example, the file is placed inside the folders `assets/CSS/blocks`.
 -->

まず、ブロック名と同名の新しい CSS ファイルを作成します: `latest-comments.css`。
ファイルの保存場所は、あなたのテーマファイルの構成方法によって異なります。本例では、ファイルは `assets/CSS/blocks` フォルダー内に配置されています。

<!-- 
The CSS class for the time element is `wp-block-latest-comments__comment-date`. The prefix and the block name are followed by the partial, separated by two underscores.
 -->

時間要素の CSS クラスは `wp-block-latest-comments__comment-date` です。接頭辞とブロック名の後には、2つのアンダースコアで区切られた、パーシャル・クラス名が続きます。

<!-- 
You can read more about the naming convention for the block editor in the [coding guidelines](https://developer.wordpress.org/block-editor/contributors/code/coding-guidelines/#naming).
 -->

ブロック・エディターの命名規則についての詳細は、[コーディング・ガイドライン](https://developer.wordpress.org/block-editor/contributors/code/coding-guidelines/#naming) でご覧いただけます。

<!-- 
The text color and font size are added with CSS custom properties that are generated from `theme.json`:
 -->

テキストの色とフォントサイズは、`theme.json` から生成される、CSS カスタム・プロパティで追加されます:

```css
.wp-block-latest-comments__comment-date {
	color: var(--wp--preset--color--primary);
	font-size: var(--wp--preset--font-size--small);
}
```

<!-- 
Next, enqueue the block style inside the themes setup function.
 -->

次に、テーマの設定関数内でブロック・スタイルをエンキューします。

<!-- 
The block name is placed inside an array to load more than one block style.  
A `foreach` loop walks through each block in the array and creates a handle, src (source), and path argument.  
`wp_enqueue_block_style()` then enqueues the file using the block name and argument:  
`wp_enqueue_block_style( "prefix/blockname", $args );`
 -->

ブロック名は配列内に配置され、複数のブロック・スタイルをロードします。
`foreach` ループが配列内の各ブロックを順に処理し、ハンドル、src (ソース)、`path` 引数を作成します。
その後、`wp_enqueue_block_style()` がブロック名と引数を使用してファイルをエンキューします:  
`wp_enqueue_block_style( "prefix/blockname", $args );`

<!-- 
In the code example, the prefix is “core” since the style is for a core block. When you style blocks from plugins, you need to adjust the prefix.
 -->

コード例では、スタイルがコア・ブロック用であるため、接頭辞は「core」です。プラグイン由来のブロックをスタイル設定する際は、接頭辞を調整する必要があります。

```php
function myfirsttheme_setup() {
	/*
	 * Load additional block styles.
	 */
	$styled_blocks = ['latest-comments'];
	foreach ( $styled_blocks as $block_name ) {
		$args = array(
			'handle' => "myfirsttheme-$block_name",
			'src'    => get_theme_file_uri( "assets/css/blocks/$block_name.css" ),
			$args['path'] = get_theme_file_path( "assets/css/blocks/$block_name.css" ),
		);
		wp_enqueue_block_style( "core/$block_name", $args );
	}
}
add_action( 'after_setup_theme', 'myfirsttheme_setup' );
```

<!-- 
### Scripts
 -->

### スクリプト

<!-- 
Any additional JavaScript files required by a theme should be loaded using `wp_enqueue_script`. This ensures proper loading and caching, and allows the use conditional tags to target specific pages. These are **optional**.
 -->

テーマで必要な追加の JavaScript ファイルは、`wp_enqueue_script` を使用してロードする必要があります。これにより、適切なロードとキャッシュが保証され、特定のページを対象とする条件付きタグの使用が可能になります。これらは **任意** です。

<!-- 
`wp_enqueue_script` uses a similar syntax to `wp_enqueue_style`.
 -->

`wp_enqueue_script` は、`wp_enqueue_style` と同様の構文を使用します。

<!-- 
Enqueue your script:
 -->

あなたのスクリプトを、エンキューします:

```php
wp_enqueue_script( $handle, $src, $deps, $ver, $args );
```

<!-- 
*   **$handle** is the name for the script.
*   **$src** defines where the script is located.
*   **$deps** is an array that can handle any script that your new script depends on, such as jQuery.
*   **$ver** lets you list a version number.
*   **$args** an array of arguments that define footer printing (via an `in_footer` key) and script loading strategies (via a `strategy` key) such as `defer` or `async`. This replaces/overloads the `$in_footer` parameter as of WordPress version 6.3.
 -->

*   **$handle** スクリプトの名称です。
*   **$src** スクリプトの保存場所を定義します。
*   **$deps** これは配列で、新規スクリプトが依存する (jQuery などの) 他のスクリプトを指定できます。
*   **$ver** バージョン番号を指定します。
*   **$args** (`in_footer` キー経由) フッター出力や (`strategy` キー経由) スクリプト・ロード戦略 (`defer` や `async` など) を定義する、引数の配列です。WordPress v6.3以降、これは `$in_footer` パラメータを置換/オーバーロードします。

<!-- 
Your enqueue function may look like this:
 -->

あなたのエンキュー関数は、次のようなものになるかもしれません:

```php
wp_enqueue_script( 'script', get_template_directory_uri() . '/js/script.js', array( 'jquery' ), 1.1, true);
```

<!-- 
### Delayed Script Loading
 -->

### スクリプト・ローディングの遅延

<!-- 
WordPress provides support for specifying a script loading strategy via the `wp_register_script()` and `wp_enqueue_script()` functions, by way of the `strategy` key within the new `$args` array parameter introduced in WordPress 6.3.
 -->

WordPress v6.3で導入された新しい `$args` 配列パラメータ内の `strategy` キー経由で、`wp_register_script()` および `wp_enqueue_script()` 関数による、スクリプトロード戦略の指定をサポートしています。

<!-- 
Supported strategies are as follows:
 -->

サポート対象の戦略は、以下の通りです:

<!-- 
*   **defer**
    *   Added by specifying an array key value pair of `'strategy' => 'defer'` to the $args parameter.
    *   Scripts marked for deferred execution — via the `defer` script attribute — are only executed once the DOM tree has fully loaded (but before the `DOMContentLoaded` and window load events). Deferred scripts are executed in the same order they were printed/added in the DOM, unlike asynchronous scripts.
*   **async**
    *   Added by specifying an array key value pair of `'strategy' => 'async'` to the `$args` parameter.
    *   Scripts marked for asynchronous execution — via the `async` script attribute — are executed as soon as they are loaded by the browser. Asynchronous scripts do not have a guaranteed execution order, as script B (although added to the DOM after script A) may execute first given that it may complete loading prior to script A. Such scripts may execute either before the DOM has been fully constructed or after the `DOMContentLoaded` event.
 -->

*   **defer**
    *   `'strategy' => 'defer'` の配列キー値ペアを、`$args` パラメータに指定して、追加します。
    *   — スクリプト属性 `defer` 経由で — 遅延実行が指定されたスクリプトは、DOM ツリーが完全にロードされた後 (ただし、`DOMContentLoaded` およびウィンドウ・ロード・イベントの前) にのみ実行されます。遅延スクリプトは、非同期スクリプトとは異なり、DOM に出力/追加された順序で実行されます。
*   **async**
    *   `'strategy' => 'async'` の配列キー値ペアを、`$args` パラメータに指定して、追加します。
    *   — スクリプト属性 `async` 経由で — 非同期実行が指定されたスクリプトは、ブラウザーによってロードされ次第実行されます。非同期スクリプトの実行順序は保証されず、(スクリプト A の後に DOM に追加された場合でも) スクリプト B がスクリプト A より先にロードを完了すれば、先に実行される可能性があります。このようなスクリプトは、DOM が完全に構築される前、または `DOMContentLoaded` イベント発生後に実行される場合があります。

<!-- 
Following is an example of specifying a loading strategy during script registration:
 -->

以下は、スクリプト登録時にロード戦略を指定する例です:

```php
wp_register_script( 
    'foo', 
    '/path/to/foo.js', 
    array(), 
    '1.0.0', 
    array( 
        'strategy'  => 'defer',
    )
);
```

<!-- 
The same approach applies when using `wp_enqueue_script()`.
 -->

`wp_enqueue_script()` を使用する場合も、同じアプローチが適用されます。

<!-- 
When specifying a delayed script loading strategy, consideration of the script’s dependency tree (its dependencies and/or dependents) is taken into account when deciding on an “eligible strategy” so as not to result in application of a strategy that is valid for one script but detrimental to others in the tree by causing an unintended out of order of execution. As a result of such logic, the intended loading strategy that you pass via the `$args` parameter may not be the final (chosen) strategy, but it will never be detrimental to (or stricter than) the intended strategy.
 -->

遅延スクリプト・ロード戦略を指定する際には、スクリプトの依存関係ツリー (依存関係および/または依存先) を考慮に入れ、「適格な戦略」を決定することにより、あるスクリプトには有効だがツリー内の他のスクリプトに悪影響を及ぼす (意図しない実行順序の乱れを引き起こす) 戦略が適用される事態を回避できます。このようなロジックの結果、`$args` パラメータ経由で渡した意図するロード戦略が最終 (選択) 戦略とはならない場合がありますが、意図した戦略に悪影響を与える (またはそれより厳格な) 戦略が選択されることは、決してありません。

<!-- 
### The Comment Reply Script
 -->

### コメント返信スクリプト

<!-- 
WordPress comments have quite a bit of functionality in them right out of the box, including threaded comments and enhanced comment forms. In order for comments to work properly, they require some JavaScript. However, since there are certain options that need to be defined within this JavaScript, the comment-reply script should be added to every classic theme that uses comments.
 -->

WordPress のコメント機能は、スレッド形式のコメントや強化されたコメント・フォームなど、すぐに使える状態でかなりの機能を備えています。コメントが正常に動作するためには、JavaScript がいくつか必要です。ただし、この JavaScript 内で定義すべき特定のオプションがあるため、コメント機能を使用するすべてのクラシック・テーマには、コメント返信スクリプトを追加する必要があります。

<!-- 
**In block themes, the script is included when you place a comment block. You do not need to add it manually.**
 -->

**ブロック・テーマでは、コメントブロックを配置するとスクリプトが自動的にインクルードされます。手動で追加する必要はありません。**

<!-- 
The proper way to include comment reply in classic themes is to use conditional tags to check if certain conditions exist, so that the script isn’t being loaded unnecessarily. For instance, you can only load scripts on single post pages using `[is_singular](https://developer.wordpress.org/reference/functions/is_singular/)`, and check to make sure that “Enable threaded comments” is selected by the user. So you can set up a function like:
 -->

クラシック・テーマでコメント返信を適切にインクルードする方法は、条件付きタグを使用して特定の条件が存在するかどうかを確認し、スクリプトが必要以上にロードされないようにすることです。たとえば、`[is_singular](https://developer.wordpress.org/reference/functions/is_singular/)` を使用して個別投稿ページでのみスクリプトをロードし、「コメントのスレッド (入れ子) を有効にする」がユーザーによって選択されていることを、確認できます。そこで、次のような関数を設定できます:

```php
if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
	wp_enqueue_script( 'comment-reply' );
}
```

<!-- 
If comments are enabled by the user, and we are on a post page, then the comment reply script will be loaded. Otherwise, it will not.
 -->

ユーザーがコメントを有効にしている場合、かつ投稿ページにいる場合、コメント返信スクリプトがロードされます。その他の場合はロードされません。

<!-- 
### Combining Enqueue Functions
 -->

### エンキュー関数の組み合わせ

<!-- 
It is best to combine all enqueued scripts and styles into a single function, and then call them using the `wp_enqueue_scripts` action. This function and action should be located somewhere below the initial setup (performed above):
 -->

すべてのエンキューされたスクリプトとスタイルを単一の関数にまとめ、`wp_enqueue_scripts` アクションを使用して呼び出すのが最善です。本関数とアクションは、(上記で実施した) 初期セットアップ以下のどこかに保存する必要があります:

```php
function add_theme_scripts() {
	wp_enqueue_style( 'style', get_stylesheet_uri() );

	wp_enqueue_style( 'slider', get_template_directory_uri() . '/css/slider.css', array(), '1.1', 'all' );

	wp_enqueue_script( 'script', get_template_directory_uri() . '/js/script.js', array( 'jquery' ), 1.1, true );

	if ( is_singular() && comments_open() && get_option( 'thread_comments' ) ) {
		wp_enqueue_script( 'comment-reply' );
	}
}
add_action( 'wp_enqueue_scripts', 'add_theme_scripts' );
```

<!-- 
## Default Scripts Included and Registered by WordPress
 -->

## WordPress によってインクルードおよび登録される、デフォルト・スクリプト

<!-- 
By default, WordPress includes many popular scripts commonly used by web developers, as well as the scripts used by WordPress itself. Some of them are listed on this reference page:
 -->

デフォルトでは、WordPress には Web 開発者が一般的に使用する多くの人気スクリプトに加え、WordPress 自体で使用されるスクリプトが、いくつかインクルードされています。その一部は、このリファレンス・ページに記載されています:

<!-- 
> [wp\_enqueue\_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script/)
 -->

> [wp\_enqueue\_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script/)

<!-- 
**The list is far from complete.** You can find a full list of included files in [wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php).
 -->

**このリストは、完全とは程遠いものです。** インクルード・ファイルの完全なリストは、[wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php) で確認できます。

/

<!-- 
Changelog:
 -->

Changelog:

<!-- 
*   Updated 2023-02-24: Added information about [wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) .
*   Updated 2024-06-06: Added alert to point readers to new doc.
 -->

*   2023-02-24更新: [wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) に関する情報を追加しました。
*   2024-06-06更新: 読者に新しいドキュメントを参照するよう促す、注意書きを追加しました。