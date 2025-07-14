<!-- 
# Including Assets
 -->

# アセットを含める

<!-- 
Many block themes do not need to load any assets. For design aspects, specifically, much of this can be handled through the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) system. But there are times when you might need to include a CSS stylesheet, custom JavaScript file, or even other types of media.
 -->

多くのブロック・テーマは、アセットをロードする必要がありません。デザイン面では、特に [グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) システムを通じて、多くの部分を処理できます。ただし、CSS スタイルシート、カスタム JavaScript ファイル、またはその他の種類のメディアを組み込む必要がある場合もあります。

<!-- 
If you are familiar with HTML, you might be accustomed to including CSS stylesheets via the `<link rel=”stylesheet”/>` or `<style>` tags. The same might be true for including JavaScript via the `<script>` tag. But you should never manually hard code these HTML elements in your theme. 
 -->

HTML に慣れている場合、`<link rel=”stylesheet”/>` や `<style>` タグを使用して CSS スタイルシートを組み込むことに慣れているかもしれません。同様のことが、`<script>` タグを使用して JavaScript を組み込む場合にも当てはまるかもしれません。しかし、あなたのテーマにこれらの HTML 要素を手動で直接記述することは絶対に避けてください。

<!-- 
WordPress has specific hooks for determining when to load scripts/styles and functions for generating the markup. This ensures that WordPress, any active plugins, and your theme all play nicely together.
 -->

WordPress には、スクリプト/スタイルのロード・タイミングやマークアップを生成する関数の実行タイミングを決定するための特定のフックが用意されています。これにより、WordPress、有効化されているプラグイン、そしてあなたのテーマがすべてうまく連携します。

<!-- 
In this document, you will learn the necessary functions for generating the proper URL to point to asset files and how to include scripts, styles, and other assets in your theme. 
 -->

このドキュメントでは、アセットファイルを指す適切な URL を生成するために必要な関数と、あなたのテーマにスクリプト、スタイル、その他のアセットを埋め込む方法について学びます。 

<!-- 
This documentation is a leap forward in comparison to some of the previous pages in the Core Concepts chapter. You will need some baseline PHP and HTML knowledge to follow along. You must also understand how to use your [theme’s `functions.php` file](https://developer.wordpress.org/themes/core-concepts/custom-functionality/). This is necessary for loading CSS stylesheet and JavaScript files.
 -->

このドキュメントは、コアコンセプト章の過去のページと比べて大きな飛躍を遂げています。この内容を理解するためには、基本的な PHP と HTML の知識が必要です。また、あなたの [テーマの `functions.php` ファイル](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) の使用方法も理解する必要があります。これは、CSS スタイルシートと JavaScript ファイルをロードするために必要です。

<!-- 
## URL and directory path functions
 -->

## URL およびディレクトリ・パス関数

<!-- 
Before including assets, you should become familiar with some of the utility functions that WordPress provides for getting URLs and directory paths within a theme. You should always use these helper functions when including any type of asset to ensure the URL or path is correct.
 -->

アセットを含める前に、WordPress がテーマ内の URL やディレクトリパスを取得するために提供するユーティリティ関数についてよく理解しておく必要があります。アセットを含める場合は、URL やパスが正しいことを確認するために、常にこれらのヘルパー関数を使用してください。

<!-- 
Three of the primary URL helper functions are:
 -->

主要な URL ヘルパー関数には以下の3つがあります:

<!-- 
*   [`get_stylesheet_uri()`](https://developer.wordpress.org/reference/functions/get_stylesheet_uri/): Returns the active theme’s `style.css` file URL.
*   [`get_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/): Returns the active theme’s URL, with an optional `$file` parameter. Falls back to the parent theme if a child theme is active and the file doesn’t exist.
*   [`get_parent_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/): Returns the parent theme’s URL, with an optional `$file` path.
 -->

*   [`get_stylesheet_uri()`](https://developer.wordpress.org/reference/functions/get_stylesheet_uri/): 有効化されているテーマの `style.css` ファイルの URL を返します。
*   [`get_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/): 有効化されているテーマの URL を返し、必要に応じて `$file` パラメータを指定できます。子テーマが有効化されていてそのファイルが存在しない場合、親テーマにフォールバックします。
*   [`get_parent_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/): 親テーマの URL を返し、必要に応じて `$file` パラメータを指定できます。

<!-- 
For directory paths, which are needed less often for assets, there are two primary functions:
 -->

アセットよりは頻繁に必要とされないディレクトリ・パスに関しては、主に2つの関数があります:

<!-- 
*   [`get_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_path/): Returns the active theme’s directory path, with an optional `$file` parameter. Falls back to the parent theme if a child theme is active and the file doesn’t exist.
*   [`get_parent_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/): Returns the parent theme’s directory path, with an optional `$file` parameter.
 -->

*   [`get_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_path/): 有効化されているテーマのディレクトリ・パスを返し、必要に応じて `$file` パラメータを指定できます。子テーマが有効化されていてそのファイルが存在しない場合、親テーマにフォールバックします。
*   [`get_parent_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/): 親テーマのディレクトリ・パスを返し、必要に応じて `$file` パラメータを指定できます。

<!-- 
## Including CSS
 -->

## CSS を含める

<!-- 
[`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) is the primary function for enqueueing a stylesheet, which tells WordPress that you want to put it in the queue to load. You would use this function within an action hook callback in your `functions.php` file, which you learned about in [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/). You’ll learn which action hooks to use for specific scenarios in the next sections.
 -->

[`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) は、スタイルシートをキューに入れるための主要な関数で、WordPress に、ロードするキューにスタイルシートを入れることを指示します。この関数は、[カスタム機能](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) で学んだ、あなたの `functions.php` ファイル内のアクションフック・コールバック内で使用します。特定のシナリオでどのアクションフックを使用すべきかは、次のセクションで学びます。

<!-- 
Take a look at the function signature:
 -->

関数シグネチャを確認してみましょう:

```php
wp_enqueue_style( 
	string $handle, 
	string $src           = '', 
	string[] $deps        = array(), 
	string|bool|null $ver = false, 
	string $media         = 'all'
);
```

<!-- 
You can use these parameters:
 -->

以下のパラメータを使用できます:

<!-- 
*   **`$handle`** is a unique name/ID for the stylesheet and should be prefixed with your theme slug.
*   **`$src`** is the file URL of your stylesheet. While it is technically an optional parameter, it is required to actually load a specific stylesheet.
*   **`$deps`** is an optional array of other stylesheet handles that your stylesheet is dependent upon.
*   **`$ver`** sets the version number of your stylesheet and is used for cache busting. Defaults to the current WordPress version.
*   **`$media`** is for specifying which type of media to load this stylesheet for, such as `all` (default), `screen`, `print`, or `handheld`.
 -->

*   **`$handle`** は、スタイルシートのユニークな名前/ID であり、あなたのテーマのスラッグで接頭辞を付ける必要があります。
*   **`$src`** は、あなたのスタイルシートのファイル URL です。技術的にはオプショナルなパラメータですが、特定のスタイルシートを実際にロードするためには必須です。
*   **`$deps`** は、あなたのスタイルシートが依存する、他のスタイルシートのハンドルを指定するオプショナルな配列です。
*   **`$ver`** は、あなたのスタイルシートのバージョン番号を設定し、キャッシュの破棄に使用されます。デフォルトは現在の WordPress バージョンです。
*   **`$media`** は、このスタイルシートを、どの種類のメディア、たとえば、`all` (デフォルト)、`screen`、`print` や `handheld` など、に適用するかを指定するためのものです。

<!-- 
If you were enqueuing a stylesheet located at `/assets/css/example.css` in your theme, your function call might look like this:
 -->

あなたのテーマ内の `/assets/css/example.css` にあるスタイルシートをキューに追加する場合、関数呼び出しは次のような形になるかもしれません:

```php
wp_enqueue_style( 
	'theme-slug-example',
	get_parent_theme_file_uri( 'assets/css/example.css' ),
	array(),
	wp_get_theme()->get( 'Version' ),
	'all'
);
```

<!-- 
The above code uses [`wp_get_theme()`](https://developer.wordpress.org/reference/functions/wp_get_theme/) to grab the theme’s version number for cache busting, but you can leave it at the default or use something custom altogether.
 -->

上記のコードでは、キャッシュ破棄の目的でテーマのバージョン番号を取得するために [`wp_get_theme()`](https://developer.wordpress.org/reference/functions/wp_get_theme/) を使用していますが、デフォルトのままにしたり、完全にカスタムのものも使用できます。

<!-- 
### Front-end stylesheets
 -->

### フロントエンド・スタイルシート

<!-- 
When loading stylesheets on the front end of a website, you will use the [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) hook for most scenarios.
 -->

Web サイトのフロントエンドでスタイルシートをロードする際、ほとんどのシナリオでは [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) フックを使用します。

<!-- 
Let’s assume that you wanted to load your theme’s `style.css` file using the `get_stylesheet_uri()` function. You would do this by adding the following code to your `functions.php` file:
 -->

`get_stylesheet_uri()` 関数を使用してあなたのテーマの `style.css` ファイルをロードしたい場合、次のようにします。`functions.php` ファイルに、以下のコードを追加します:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style( 
		'theme-slug-style', 
		get_stylesheet_uri()
	);
}
```

<!-- 
Remember that you can also pass other parameters to the `wp_enqueue_style()` function if needed. The above code is the minimum needed to load the stylesheet.
 -->

必要に応じて、`wp_enqueue_style()` 関数に他のパラメータを指定できることも覚えておいてください。上記のコードは、スタイルシートをロードするために必要な最小限のコードです。

<!-- 
Let’s further suppose that you wanted to load a second stylesheet located at `/assets/css/primary.css` in your theme. For this, you would use the `get_parent_theme_file_uri()` function to get the correct URL. 
 -->

さらに、あなたのテーマ内の `/assets/css/primary.css` にある2つ目のスタイルシートをロードしたい場合を想定しましょう。この場合、`get_parent_theme_file_uri()` 関数を使用して正しい URL を取得します。

<!-- 
Here is what your code would look like with both stylesheets enqueued:
 -->

以下は、両方のスタイルシートをキューに追加した際のコードの例です:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style(
		'theme-slug-style', 
		get_stylesheet_uri()
	);

	wp_enqueue_style( 
		'theme-slug-primary',
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	);
}
```

<!-- 
### Inline styles
 -->

### インライン・スタイル

<!-- 
There are times when you might need to add some inline CSS to the `<head>` area on the front end. WordPress has the [`wp_add_inline_style()`](https://developer.wordpress.org/reference/functions/wp_add_inline_style/) function for this specific scenario.
 -->

フロントエンドの `<head>` エリアにインライン CSS を追加する必要がある場合があります。WordPress には、この特定のシナリオのための [`wp_add_inline_style()`](https://developer.wordpress.org/reference/functions/wp_add_inline_style/) 関数があります。

<!-- 
Here is a look at the function signature:
 -->

以下は関数シグネチャの概要です:

```php
wp_add_inline_style( 
	string $handle, 
	string $data 
);
```

<!-- 
In this case, you must pass in a `$handle` parameter that matches a handle of an existing stylesheet that is enqueued for the page. The `$data` parameter is your custom CSS code.
 -->

この場合、該当するページでキューに追加されている既存のスタイルシートのハンドルと一致する `$handle` パラメータを指定する必要があります。`$data` パラメータは、あなたのカスタム CSS コードです。

<!-- 
Let’s extend the code from the previous section by adding a small bit of CSS that sets the body background color to a light gray:
 -->

前のセクションのコードを拡張し、ボディの背景色を薄い灰色に設定する小さな CSS を追加しましょう:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style(
		'theme-slug-style', 
		get_stylesheet_uri()
	);

	wp_enqueue_style( 
		'theme-slug-primary',
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	);

	wp_add_inline_style( 
		'theme-slug-primary', 
		'body { background: #eee; }'
	);
}
```

<!-- 
In the `wp_add_inline_style()` function call, the code uses the existing `theme-slug-primary` handle to attach an inline style.
 -->

`wp_add_inline_style()` 関数呼び出しにおいて、コードは既存の `theme-slug-primary` ハンドルを使用してインライン・スタイルを紐付けます。

<!-- 
### Editor stylesheets
 -->

### エディター・スタイルシート

<!-- 
When creating a theme with custom CSS on the front end, you will almost always want your custom styles to also appear in the editor. This will create a consistent user experience across the site. But WordPress does not automatically load your front-end stylesheets in the editor.
 -->

フロントエンドでカスタム CSS を使用してテーマを制作する場合、ほとんどの場合、カスタム・スタイルをエディターにも表示したいと思うでしょう。これにより、サイト全体で一貫したユーザーエクスペリエンスを実現できます。しかし、WordPress は、フロントエンドのスタイルシートをエディターに自動的にロードしません。

<!-- 
For that, you will need to use the [`add_editor_style()`](https://developer.wordpress.org/reference/functions/add_editor_style/) function:
 -->

そのため、以下の [`add_editor_style()`](https://developer.wordpress.org/reference/functions/add_editor_style/) 関数を使用する必要があります:

```php
add_editor_style( array|string $stylesheet = 'editor-style.css' );
```

<!-- 
It accepts a single parameter of `$stylesheet`, which can be a single stylesheet filename or an array of filenames. These can be relative to the theme folder or a full URL.
 -->

この関数は、シングル・パラメータとして `$stylesheet` を受け付け、これは、単一のスタイルシート・ファイル名またはファイル名の配列である可能性があります。これらは、テーマフォルダーに対する相対パスまたはフル URL のどちらでも指定可能です。

<!-- 
Note that when using relative URLs, a file in the child theme with the same filename will take priority. That’s why it’s generally best practice to use the full stylesheet URL.
 -->

相対 URL を使用する場合、子テーマ内の同じファイル名を持つファイルが優先されます。そのため、一般的にベスト・プラクティスとして、スタイルシートのフル URL を使用することが推奨されます。

<!-- 
This code snippet shows how to add the active theme’s main `style.css` file as an editor style:
 -->

このコードスニペットは、有効化されているテーマのメイン `style.css` ファイルを、エディタースタイルとして追加する方法を示しています:

```php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_editor_style( get_stylesheet_uri() );
}
```

<!-- 
If you wanted to add both the `style.css` file and `primary.css` from the earlier examples, you could pass them in as an array:
 -->

以前の例で示した `style.css` ファイルと `primary.css` ファイルを両方追加したい場合、それらを配列として渡すことができます:

```php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_editor_style( array(
		get_stylesheet_uri(),
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	) );
}
```

<!-- 
### Block stylesheets
 -->

### ブロック・スタイルシート

<!-- 
WordPress also includes a [`wp_enqueue_block_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) function for loading per-block stylesheets in the editor and on the front end. This is covered in full detail in the [Block Stylesheets](https://developer.wordpress.org/themes/features/block-stylesheets/) documentation.
 -->

WordPress には、エディターおよびフロントエンドで、ブロックごとのスタイルシートをロードするための [`wp_enqueue_block_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) 関数も搭載されています。これは [ブロック・スタイルシート](https://developer.wordpress.org/themes/features/block-stylesheets/) ドキュメントで詳しく説明されています。

<!-- 
For an advanced exploration of block stylesheets, read [Leveraging theme.json and per-block styles for more performant themes](https://developer.wordpress.org/news/2022/12/leveraging-theme-json-and-per-block-styles-for-more-performant-themes/) on the WordPress Developer Blog.
 -->

ブロックスタイルシートの詳細については、WordPress 開発者ブログ [theme.json とブロックごとのスタイルを活用して、よりパフォーマンスの高いテーマを作成しよう](https://developer.wordpress.org/news/2022/12/leveraging-theme-json-and-per-block-styles-for-more-performant-themes/) をご覧ください。

<!-- 
## Including JavaScript
 -->

## JavaScript を含める

<!-- 
Like stylesheets, WordPress has a primary function for enqueueing JavaScript files: [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/). You would also use this function within an action hook callback in your `functions.php` file, and you’ll learn which hooks to use in the following sections.
 -->

スタイルシートと同様に、WordPress には JavaScript ファイルをキューに入れるための主要な関数があります: [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) です。この関数は、あなたの `functions.php` ファイル内のアクションフック・コールバック内でも使用し、どのフックを使用すべきかは、以下のセクションで説明します。

<!-- 
Take a look at the function signature:
 -->

関数シグネチャを確認してみましょう:

```php
wp_enqueue_script( 
	string $handle, 
	string $src           = '', 
	string[] $deps        = array(), 
	string|bool|null $ver = false, 
	array|bool $in_footer = false
);
```

<!-- 
You can use these parameters:
 -->

以下のパラメータを使用できます:

<!-- 
*   **`$handle`:** A unique name/ID for the script and should be prefixed with your theme slug.
*   **`$src`:** The file URL of your script. While it is technically an optional parameter, it is required to actually load a specific script
*   **`$deps`:** An optional array of other script handles that your script is dependent upon.
*   **`$ver`:** Sets the version number of your script and is used for cache busting. Defaults to the current WordPress version.
*   **`$in_footer`:** Determines whether to load the script in the header or footer. As of WordPress 6.3, this parameter accepts an array of values:
    *   **`strategy`:** Accepts either `'defer'` (default) or `'async'` to set the script-loading strategy.
    *   **`in_footer`:** A boolean value to determine whether to load the script in the header or footer.
 -->

*   **`$handle`:** スクリプトのユニークな名前/ID であり、あなたのテーマのスラッグで接頭辞を付ける必要があります。
*   **`$src`:** あなたのスクリプトのファイル URL です。技術的にはオプショナルなパラメータですが、特定のスクリプトを実際にロードするためには必須です。
*   **`$deps`:** あなたのスクリプトが依存する、他のスクリプトのハンドルを指定するオプショナルな配列です。
*   **`$ver`:** あなたのスクリプトのバージョン番号を設定し、キャッシュの破棄に使用されます。デフォルトは現在の WordPress バージョンです。
*   **`$in_footer`:** スクリプトをヘッダーにロードするかフッターにロードするかを決定します。WordPress 6.3以降、このパラメータは値の配列を受け付けます:
    *   **`strategy`:** `'defer'` (デフォルト) や `'async'` のいずれかを指定して、スクリプトのロード戦略を設定します。
    *   **`in_footer`:** スクリプトをヘッダーまたはフッターにロードするかどうかを決定する、真偽値です。

<!-- 
If you were enqueuing a script located at `/assets/js/example.js` in your theme, your function call might look like this:
 -->

あなたのテーマ内の `/assets/js/example.js` にあるスクリプトをキューに追加する場合、関数呼び出しは次のような形になるかもしれません:

```php
wp_enqueue_script( 
	'theme-slug-example',
	get_parent_theme_file_uri( 'assets/js/example.js' ),
	array(),
	wp_get_theme()->get( 'Version' ),
	true
);
```

<!-- 
### Front-end JavaScript
 -->

### フロントエンド JavaScript

<!-- 
When loading stylesheets on the front end of a website, you will use the [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) hook for most scenarios.
 -->

Web サイトのフロントエンドでスタイルシートをロードする際、ほとんどのシナリオでは [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) フックを使用します。

<!-- 
Suppose you had a custom navigation script located at `assets/js/navigations.js` in your theme. For this, you would use the `get_parent_theme_file_uri()` function to get the correct URL. 
 -->

あなたのテーマ内の `assets/js/navigations.js` にカスタム・ナビゲーション・スクリプトがあるとします。この場合、正しい URL を取得するために `get_parent_theme_file_uri()` 関数を使用します。

<!-- 
Here is what your function would look like when enqueueing the script:
 -->

スクリプトをキューに追加する際、あなたの関数は以下のようになります:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_scripts' );

function theme_slug_enqueue_scripts() {
	wp_enqueue_script( 
		'theme-slug-navigation',
		get_parent_theme_file_uri( 'assets/js/navigation.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);
}
```

<!-- 
### Inline JavaScript
 -->

### インライン JavaScript

<!-- 
Sometimes you might want to add some inline JavaScript to the `<head>` area on the front end. WordPress has the [`wp_add_inline_script()`](https://developer.wordpress.org/reference/functions/wp_add_inline_script/) function for this purpose.
 -->

フロントエンドの `<head>` エリアにインライン JavaScript を追加したい場合もあるでしょう。WordPress には、この目的のための [`wp_add_inline_script()`](https://developer.wordpress.org/reference/functions/wp_add_inline_script/) 関数があります。

<!-- 
Take a look at the function signature:
 -->

関数シグネチャを確認してみましょう:

```php
wp_add_inline_script( 
	string $handle, 
	string $data, 
	string $position = 'after' 
);
```

<!-- 
Like its counterpart for styles, you must attach this to an enqueued script via the `$handle` parameter. The secondary parameter, `$data`, should be the JavaScript code itself. The difference here is the addition of a third parameter, `$position`, which lets you position the inline script before or after the script that it is attached to.
 -->

スタイル用の対応するものと同様、キューに追加された既存のスクリプトに、これを `$handle` パラメータ経由で追加する必要があります。第2のパラメータ `$data` は、JavaScript コード自体である必要があります。ここでの違いは、第3のパラメータ `$position` の追加で、これにより、追加されたスクリプトの前後どちらかにインラインスクリプトを配置できます。

<!-- 
The following code builds on top of the navigation script from the previous section by adding an inline script to it:
 -->

以下のコードは、前のセクションのナビゲーション・スクリプトをもとに、それにインライン・スクリプトを追加することで構築します:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_scripts' );

function theme_slug_enqueue_scripts() {
	wp_enqueue_script( 
		'theme-slug-navigation',
		get_parent_theme_file_uri( 'assets/js/navigation.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);

	wp_add_inline_script( 
		'theme-slug-navigation', 
		'console.log( "Testing" );'
	);
}
```

<!-- 
In the `wp_add_inline_script()` function call, the code uses the existing `theme-slug-navigation` handle to attach the inline style.
 -->

`wp_add_inline_script()` 関数呼び出しにおいて、コードは既存の `theme-slug-navigation` ハンドルを使用してインライン・スタイルを紐付けます。

<!-- 
### Editor JavaScript
 -->

### エディター JavaScript

<!-- 
When you need to load a JavaScript file for the block editor, you must use the [`enqueue_block_editor_assets`](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) hook. Note that this is for loading scripts on the admin page itself and not within the content iframe.
 -->

ブロック・エディター用 JavaScript ファイルをロードする必要がある場合、必ず [`enqueue_block_editor_assets`](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) フックを使用する必要があります。これは、管理画面それ自体でスクリプトをロードするためのものであり、コンテンツの iframe 内での使用ではありません。

<!-- 
Suppose you had an `assets/js/editor.js` file that you needed to load for the editor. Your code should look like this:
 -->

エディターでロードする必要がある `assets/js/editor.js` ファイルがあると仮定します。コードは次のようにします:

```php
add_action( 'enqueue_block_editor_assets', 'theme_slug_enqueue_editor_scripts' );

function theme_slug_enqueue_editor_scripts() {
	wp_enqueue_script( 
		'theme-slug-editor',
		get_parent_theme_file_uri( 'assets/js/editor.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);
}
```

<!-- 
Generally, themes wouldn’t need to load JavaScript for the editor itself. But for advanced use cases, it may be necessary. It is also recommended to integrate with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package for easier management. For more information on how to do this, read [Beyond block styles, part 1: using the WordPress scripts package with themes](https://developer.wordpress.org/news/2023/07/beyond-block-styles-part-1-using-the-wordpress-scripts-package-with-themes/).
 -->

通常、テーマではエディター自体用に JavaScript をロードする必要はありません。しかし、高度なユースケースでは、それが必要になる場合もあります。また、管理を容易にするために、[`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) パッケージと統合することをおすすめします。この方法の詳細については、[ブロック・スタイルを超えて、パート1: テーマで WordPress スクリプトパッケージを使用する](https://developer.wordpress.org/news/2023/07/beyond-block-styles-part-1-using-the-wordpress-scripts-package-with-themes/) をご覧ください。

<!-- 
### Default WordPress scripts
 -->

### デフォルト WordPress スクリプト

<!-- 
WordPress bundles many custom and third-party scripts. You should always use these scripts if you need one of them instead of loading a custom version. This ensures that you avoid conflicts with plugins. 
 -->

WordPress には、多くのカスタム・スクリプトやサードパーティ製スクリプトがバンドルされています。これらのスクリプトのうち、必要なものがあれば、カスタムバージョンをロードする代わりに、必ずこれらのスクリプトを使用してください。そうすることで、プラグインとの競合を回避できます。

<!-- 
Some of the scripts are referenced in the [`wp_enqueue_script()` documentation](https://developer.wordpress.org/reference/functions/wp_enqueue_script/), but that list may not always be up to date. You can find the full list of included files in [wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php).
 -->

一部のスクリプトは [`wp_enqueue_script()` ドキュメント](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) で参照されていますが、そのリストは常に最新であるとは限りません。含まれるファイルの完全なリストは [wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php) で確認できます。

<!-- 
## Including images
 -->

## 画像を含める

<!-- 
Block themes will not often need to include images, except in patterns. You will learn more about these in the [Block Patterns](https://developer.wordpress.org/themes/features/block-patterns/) documentation. But for a quick overview, let’s take a look at how to reference an image in your theme.
 -->

ブロック・テーマでは、パターンの場合を除き、画像を含める必要はほとんどありません。これらの詳細については、[ブロック・パターン](https://developer.wordpress.org/themes/features/block-patterns/) ドキュメントで学ぶことができます。しかし、簡単な概要として、あなたのテーマ内で画像を参照する方法を見てみましょう。

<!-- 
Assuming you had an image file located at `assets/img/example.webp`, you would use this code to reference the correct URL:
 -->

`assets/img/example.webp` に画像ファイルが存在する場合、正しい URL を参照するには次のコードを使用します:

```php
<img src="<?php echo esc_url( get_parent_theme_file_uri( 'assets/img/example.webp' ) ); ?>" alt="" />
```

<!-- 
Note that the above example uses `get_parent_theme_file_uri()`. In most cases, this will be the correct function.
 -->

上記の例では `get_parent_theme_file_uri()` が使用されています。ほとんどのケースでは、これが正しい関数です。

<!-- 
But if you are building a child theme or a theme where you would like to allow other child theme authors to override the image, you can use `get_theme_file_uri()` instead:
 -->

ただし、子テーマを構築する場合や、他の子テーマの作者が画像を上書きできるようにしたいテーマを構築する場合、代わりに `get_theme_file_uri()` を使用できます:

```php
<img src="<?php echo esc_url( get_theme_file_uri( 'assets/img/example.webp' ) ); ?>" alt="" />
```

<!-- 
## Including fonts
 -->

## フォントを含める

<!-- 
Typically, you would expect fonts to fall directly under the assets documentation. But WordPress has special methods for loading fonts via the `theme.json` file that integrates with the editor. This documentation is under the [Typography](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) page of the Global Settings and Styles chapter.
 -->

一般的には、フォントはアセット・ドキュメントに直接含まれると予想されます。しかし、WordPress には、エディターと統合された、`theme.json` ファイルを介してフォントをロードする特別な方法があります。このドキュメントは、グローバル設定とスタイル章の [タイポグラフィ](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) ページに掲載されています。