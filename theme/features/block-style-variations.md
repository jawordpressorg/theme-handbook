<!-- 
# Block Style Variations
 -->

# ブロック・スタイル・バリエーション

<!-- 
Block style variations (block styles, for short) let you create alternate styles for individual blocks. Registered styles appear in the user interface, allowing users to quickly switch between the default style and any alternates.
 -->

ブロック・スタイル・バリエーション (ブロック・スタイルと略称) を使用すると、個々のブロックに対して代替スタイルを制作できます。登録されたスタイルはユーザーインターフェースに表示され、ユーザーはデフォルトのスタイルと代替スタイルの間をすばやく切り替えることができます。

<!-- 
Many features, unfortunately, use the term “variations” in their name. This can be confusing at times. The biggest thing to note is that block style variations are not the same thing as [global style variations](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/) and [block variations](https://developer.wordpress.org/themes/features/block-variations/).
 -->

残念ながら、多くの機能ではその名称に「バリエーション」という用語が使用されています。これは時々混乱を招くことがあります。最も重要な点は、ブロック・スタイル・バリエーションは、[グローバル・スタイル・バリエーション](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/) や [ブロック・バリエーション](https://developer.wordpress.org/themes/features/block-variations/) とは別物であるということに注意してください。

<!-- 
Often, you will see block style variations referred to as “block styles,” as they are in this article, but this should also not be confused with [block stylesheets](https://developer.wordpress.org/themes/features/block-stylesheets/). The two features can be used to work together, but they are not the same thing.
 -->

しばしばこの記事と同じように、ブロック・スタイル・バリエーションは「ブロック・スタイル」と呼ばれますが、これと [ブロック・スタイルシート](https://developer.wordpress.org/themes/features/block-stylesheets/) を混同しないでください。この2つの機能は組み合わせて使用できますが、同じものではありません。

<!-- 
## What are block styles?
 -->

## ブロック・スタイルって ?

<!-- 
Under the hood, block styles are nothing more than CSS classes added to a block’s wrapping element with the name of `.is-style-{name}`. This allows you to add custom CSS to alter the block’s design in some way.
 -->

内部的には、ブロック・スタイルは、ブロックのラップ要素に `.is-style-{name}` という名前で追加された CSS クラスに過ぎません。これにより、ブロックのデザインを何らかの形で変更するために、カスタム CSS を追加できます。

<!-- 
In this screenshot, you can see multiple block styles registered for the Image block under the **Styles** panel, and the core **Rounded** option is selected:
 -->

このスクリーンショットでは、**「スタイル」** パネル以下の「画像ブロック」に複数のブロック・スタイルが登録されており、コア **角丸** オプションが選択されています:

<!-- 
[![WordPress post editor showing an Image block with a rounded style in the content canvas.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-rounded.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-rounded.jpg?ssl=1)
 -->

[![コンテンツ・キャンバス内に、角が丸められたスタイルの「画像ブロック」が表示されている WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-rounded.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-rounded.jpg?ssl=1)

<!-- 
All that is happening here is that core WordPress and the theme have both registered block styles for the Image block, and the user has selected one of those styles. Then the CSS for that registered style is applied to a block.
 -->

ここで起こっていることは、コア WordPress とテーマの両方が「画像ブロック」用のブロック・スタイルを登録しており、ユーザーがそれらのスタイルのうちの1つを選択しただけのことです。そして、その登録されたスタイルの CSS がブロックに適用されます。

<!-- 
Ultimately, block styles are just a standard way to add a class to a block and customize it with CSS.
 -->

最終的に、ブロック・スタイルは、ブロックにクラスを追加し、CSS でカスタマイズする標準的な方法に過ぎません。

<!-- 
Users can only apply one style to a block at a time. They cannot combine them using the standard design tools. If you need to allow more options, you might consider building custom design tools. Read the [Beyond Block Styles](https://developer.wordpress.org/news/tag/beyond-block-styles/) tutorial series on the WordPress Developer Blog to learn how.
 -->

ユーザーは、一度に1つのブロックに対して1つのスタイルしか適用できません。標準のデザインツールでは、複数のスタイルを組み合わせることはできません。さらに多くのオプションを必要とする場合は、カスタムデザインツールを構築することを検討してください。WordPress 開発者ブログの [ブロック・スタイルを超えて](https://developer.wordpress.org/news/tag/beyond-block-styles/) チュートリアル・シリーズを読んで、その方法をご覧ください。

<!-- 
## PHP-based block styles
 -->

## PHP ベースのブロック・スタイル

<!-- 
Most theme authors will want to register block styles with PHP. Skip ahead to the “JavaScript-based block styles” section if you need or want to work with them via JavaScript.
 -->

ほとんどのテーマ作者は、PHP を使用してブロック・スタイルを登録したいと考えているでしょう。JavaScript を経由してそれらを取り扱う必要がある場合や希望する場合は、「JavaScript ベースのブロック・スタイル」セクションまでスキップしてください。

<!-- 
### Registering blocks styles with PHP
 -->

### PHP でブロック・スタイルの登録

<!-- 
To register a block style, use the [`register_block_style()`](https://developer.wordpress.org/reference/functions/register_block_style/) PHP  function. The function’s signature looks like this:
 -->

ブロック・スタイルを登録するには、PHP の [`register_block_style()`](https://developer.wordpress.org/reference/functions/register_block_style/) 関数を使用します。関数のシグネチャは、次のようになります:

```php
register_block_style( 
	string $block_name, 
	array $style_properties
): bool
```

<!-- 
The function accepts two parameters and returns `true` or `false`, depending on whether the registration was successful:
 -->

この関数は2つのパラメータを受け取り、登録が成功したか否かによって、`true` または `false` を返します:

<!-- 
*   **`$block_name`:** The name of the block, including both the namespace and slug (e.g., `core/image`).
*   **`$style_properties`:** An array of arguments that can be used to configure the style:
    *   **`name`:** *(Required)* A unique identifier/slug, which is used to generate the class (e.g., `is-style-{name}`).
    *   **`label`:** *(Required)* An human-readable label, which may be translated.
    *   **`inline_style`:** Inline CSS to be printed when the style is in use.
    *   **`style_handle`:** A handle for a registered stylesheet to load for the style.
    *   **`is_default`:** Whether the style should be selected as the default for the block (defaults to `false`).
 -->

*   **`$block_name`:** 名前空間とスラッグを含む、ブロックの名称です (例: `core/image`)。
*   **`$style_properties`:** スタイルを構成するために使用できる、引数の配列です:
    *   **`name`:** *(必須)* クラスを生成するために使用される、一意の識別子/スラッグです (例: `is-style-{name}`)。
    *   **`label`:** *(必須)* 翻訳可能な、人間可読ラベルです。
    *   **`inline_style`:** スタイルが使用されている際に出力される、インライン CSS です。
    *   **`style_handle`:** スタイルを適用するための、登録済みスタイルシートのハンドルです。
    *   **`is_default`:** ブロックのデフォルト・スタイルとして選択するか否かです (デフォルトは `false`)。

<!-- 
`style_handle` [currently has a bug](https://github.com/WordPress/gutenberg/issues/27244#issuecomment-1407082624) where it only enqueues the stylesheet in the editor but not on the front end. Until that linked ticket is addressed, its use is not recommended.
 -->

`style_handle` には、[現在、バグがあり](https://github.com/WordPress/gutenberg/issues/27244#issuecomment-1407082624)、エディターでは、スタイルシートをキューに入れることができるが、フロントエンドでは入れることができない、という問題があります。リンク先のチケットが対処されるまで、その使用は推奨されません。

<!-- 
Let’s try creating a block style that gives the Image block a “hand drawn” look so that it looks like this when selected in the editor:
 -->

「画像ブロック」に「手描き風」のルックを付与する、ブロック・スタイルを制作してみましょう。エディターで選択した際に、以下のようになります:

<!-- 
[![WordPress post editor showing an Image block with a hand-drawn style in the content canvas.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-hand-drawn.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-hand-drawn.jpg?ssl=1)
 -->

[![コンテンツ・キャンバスに手描き風の「画像ブロック」を表示する、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-hand-drawn.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-image-hand-drawn.jpg?ssl=1)

<!-- 
To register this block style, you need to configure it via the `register_block_style()` function and add it as a callback on the `init` hook. 
 -->

このブロック・スタイルを登録するには、`register_block_style()` 関数経由で設定し、`init` フックのコールバックとして追加する必要があります。 

<!-- 
Add the following code to your theme’s `functions.php` file to test it out:
 -->

あなたのテーマの `functions.php` ファイルに以下のコードを追加して、テストしてみましょう:

```php
add_action( 'init', 'themeslug_register_block_styles' );

function themeslug_register_block_styles() {
	register_block_style( 'core/image', array(
		'name'         => 'hand-drawn',
		'label'        => __( 'Hand Drawn', 'themeslug' ),
		'inline_style' => '.wp-block-image.is-style-hand-drawn img {
			border: 2px solid currentColor;
			overflow: hidden;
			box-shadow: 0 4px  10px 0 rgba( 0, 0, 0, 0.3 );
			border-radius: 255px 15px 225px 15px/15px 225px 15px 255px !important;
		}'
    ) );
}
```

<!-- 
If your `inline_style` argument is more than a few lines of CSS code, you may want to add your CSS to a custom [block stylesheet](https://developer.wordpress.org/themes/features/block-stylesheets/) instead.
 -->

あなたの `inline_style` 引数が CSS コードの数行を超える場合、代わりにカスタム [ブロック・スタイルシート](https://developer.wordpress.org/themes/features/block-stylesheets/) に、あなたの CSS を追加することを検討してください。

<!-- 
### Unregistering block styles with PHP
 -->

### PHP でブロック・スタイルの登録解除

<!-- 
To unregister a block style that has been registered with PHP, use the [`unregister_block_style()`](https://developer.wordpress.org/reference/functions/unregister_block_style/) function. Here is a look at its signature:
 -->

PHP で登録されたブロック・スタイルを登録解除するには、[`unregister_block_style()`](https://developer.wordpress.org/reference/functions/unregister_block_style/) 関数を使用します。以下にそのシグネチャを示します:

```php
unregister_block_style(
	string $block_name, 
	string $block_style_name 
): bool
```

<!-- 
The function accepts two parameters and returns `true` or `false`, depending on whether the registration was successful:
 -->

この関数は2つのパラメータを受け取り、登録解除が成功したか否かによって、`true` または `false` を返します:

<!-- 
*   **`$block_name`:** The name of the block, including both its namespace and slug (e.g., `core/image`).
*   **`$block_style_name`:** The name/slug of a block style that was registered via PHP.
 -->

*   **`$block_name`:** 名前空間とスラッグを含む、ブロックの名称です (例: `core/image`)。
*   **`$block_style_name`:** PHP 経由で登録されたブロック・スタイルの名称/スラッグです。

<!-- 
To unregister the `hand-drawn` block style you registered earlier, you need to add an action function to the `init` hook (note the action call has a later priority of `99` so that it runs after the earlier registration function, which defaults to `10`):
 -->

以前に登録した `hand-drawn` ブロック・スタイルを登録解除するには、`init` フックにアクション関数を追加する必要があります (アクション・コールの優先度は `99` であり、これにより、デフォルトでは優先度 `10` である、以前の登録関数よりも後に実行される):

```php
add_action( 'init', 'themeslug_register_block_styles', 999 );

function themeslug_register_block_styles() {
	unregister_block_style( 'core/image', 'hand-drawn' );
}
```

<!-- 
You can only unregister block styles with PHP if they have been registered via PHP. If the block style was registered with JavaScript, you must also use JavaScript to unregister it. For more information, see the “Unregistering block styles with JavaScript” section below.
 -->

PHP 経由で登録された場合、ブロック・スタイルの登録解除は PHP のみで行うことができます。JavaScript で登録されたブロック・スタイルの場合、登録解除には JavaScript を使用する必要があります。詳細情報については、以下の「JavaScript でブロック・スタイルの登録解除」セクションを御覧ください。

<!-- 
## JavaScript-based block styles
 -->

## JavaScript ベースのブロック・スタイル

<!-- 
To register or unregister block styles via JavaScript, you need to load a JavaScript file on the `enqueue_block_editor_assets` hook.
 -->

JavaScript 経由でブロック・スタイルを登録または登録解除するには、`enqueue_block_editor_assets` フックで JavaScript ファイルをロードする必要があります。

<!-- 
First, create an `/assets/js/block-editor.js` file in your theme (you can change this name or add it anywhere, but the example below assumes this name and location).
 -->

まず、あなたのテーマ内に `/assets/js/block-editor.js` ファイルを作成します (この名称や場所は変更可能だが、以下の例では、この名称と場所を前提としている)。

<!-- 
Then add this code to your theme’s `functions.php` file to enqueue your script:
 -->

次に、あなたのテーマの `functions.php` ファイルにこのコードを追加して、あなたのスクリプトをキューに追加します:

```php
add_action( 'enqueue_block_editor_assets', 'themeslug_block_editor_assets' );

function themeslug_block_editor_assets() {
	wp_enqueue_script(
		'themeslug-block-editor',
		get_theme_file_uri( 'assets/js/block-editor.js' ),
		array( 
			'wp-blocks', 
			'wp-dom-ready', 
			'wp-edit-post' 
		)
	);
}
```

<!-- 
### Registering block styles with JavaScript
 -->

### JavaScript でブロック・スタイルの登録

<!-- 
To register a block style via JavaScript, you’ll use the `registerBlockStyle()` function, which works similarly to the `register_block_style()` PHP function. It just uses JavaScript syntax.
 -->

JavaScript を経由でブロック・スタイルを登録するには、PHP の `register_block_style()` 関数と類似した動作をする、`registerBlockStyle()` 関数を使用します。単に JavaScript の構文を使用するだけです。

<!-- 
Let’s use the same example from earlier and register a “hand drawn” Image block style. Add this code to your `/assets/js/block-editor.js` file:
 -->

先程と同じ例を使用し、「手描き」の「画像」ブロック・スタイルを登録してみましょう。このコードをあなたの `/assets/js/block-editor.js` ファイルに追加してください:

```javascript
wp.blocks.registerBlockStyle( 'core/image', {
	name: 'hand-drawn',
	label: 'Hand Drawn'
} );
```

<!-- 
You can also set the `isDefault` argument to `true` if this is meant to be the default block style (it’s `false` by default).
 -->

これをデフォルト・ブロック・スタイルとして設定する場合は、`isDefault` 引数を `true` に設定できます (デフォルトは `false`)。

<!-- 
For adding your custom CSS, you’ll need to load a custom [block stylesheet](https://developer.wordpress.org/themes/features/block-stylesheets/) or add your CSS by some other means.
 -->

あなたのカスタム CSS を追加するには、カスタム [ブロック・スタイルシート](https://developer.wordpress.org/themes/features/block-stylesheets/) をロードするか、他の方法を使用してあなたの CSS を追加する必要があります。

<!-- 
### Unregistering block styles with JavaScript
 -->

### JavaScript でブロック・スタイルの登録解除

<!-- 
There is also an `unregisterBlockStyle()` JavaScript function that is equivalent to the `unregister_block_style()` PHP function. You can use this to unregister any block styles that have been registered via JavaScript.
 -->

PHP の `unregister_block_style()` 関数と等価な、JavaScript の `unregisterBlockStyle()` 関数も存在します。この関数を使用すると、JavaScript 経由で登録されたブロック・スタイルを登録解除できます。

<!-- 
To avoid a race condition where there’s a conflict between when a block style is registered versus when it is unregistered, you need to ensure that you unregister a block style after it has already been registered. The best way to do this is to add it inside a function callback on `wp.domReady`, which ensures that you unregister after the DOM has loaded.
 -->

ブロック・スタイルが登録されたときと、ブロックスタイルが登録解除されたときとの間で、競合が発生するレース条件を回避するために、ブロック・スタイルを登録解除するには、すでに登録されているブロック・スタイルを登録解除する必要があります。これを実施する最良の方法は、`wp.domReady` の関数コールバック内に追加することで、これにより、DOM が読み込まれた後に登録解除されることが保証されます。

<!-- 
To unregister the `hand-drawn` block style that you registered via JavaScript, add this to your `/assets/js/block-editor.js` file:
 -->

JavaScript 経由で登録した `hand-drawn` ブロック・スタイルを解除するには、あなたの `/assets/js/block-editor.js` ファイルに次を追加してください:

```javascript
wp.domReady( function () {
	wp.blocks.unregisterBlockStyle( 'core/image', 'hand-drawn' );
} );
```

<!-- 
You can only unregister block styles with JavaScript if they have been registered via JavaScript. If the block style was registered with PHP, you must also use PHP to unregister it. For more information, see the “Unregistering block styles with PHP” section above.
 -->

JavaScript 経由で登録された場合、ブロック・スタイルの登録解除は JavaScript のみで実施できます。PHP で登録されたブロック・スタイルの場合、登録解除にも PHP を使用する必要があります。詳細情報については、上記の「PHP でブロック・スタイルの登録解除」セクションをご覧ください。

<!-- 
## Customizing block styles via theme.json
 -->

## theme.json 経由で、ブロック・スタイルのカスタマイズ

<!-- 
It’s possible to customize the design of the core WordPress block styles. This means that you might not need to add custom CSS at all to get the look you’re after.
 -->

コア WordPress ブロック・スタイルのデザインは、カスタマイズ可能です。つまり、希望の外観を実現するためにカスタム CSS を追加する必要はまったくないかもしれません。

<!-- 
It is also recommended to use this method if possible for your customizations because they appear in the **Appearance > Editor > Styles** interface. Plus, your theme users can make their own changes to them if desired.
 -->

この方法も、可能な場合はあなたのカスタマイズに利用することをおすすめします。なぜなら、これらのカスタマイズは **外観 > エディター > スタイル** インターフェースに表示されるためです。さらに、あなたのテーマのユーザーは、必要に応じてそれらに独自の変更を加えることができます。

<!-- 
Let’s try to modify the Outline style of core Button block so that it has a drop-shadow that creates a double-border effect:
 -->

コアの「ボタン」ブロックの「枠線」スタイルを修正し、ドロップシャドウを追加して、二重の境界線効果を実現してみましょう:

<!-- 
[![WordPress post editor with three outlined buttons in the content canvas. Each has a solid-border drop-shadow.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-button-outlined.png?resize=2400%2C1235&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-button-outlined.png?ssl=1)
 -->

[![コンテンツ・キャンバスに枠線のついたボタンが3つある、WordPress 投稿エディター。各ボタンには、実線のドロップシャドウが付いている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-button-outlined.png?resize=2400%2C1235&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-styles-button-outlined.png?ssl=1)

<!-- 
To do this, open your `theme.json` file. You’ll need to target the `styles.blocks.core/button.variations.outline` property. It works just like any other [style that you can add via `theme.json`](https://developer.wordpress.org/themes/global-settings-and-styles/styles/).
 -->

これを実施するには、あなたの `theme.json` ファイルを開きます。`styles.blocks.core/button.variations.outline` プロパティをターゲットに設定する必要があります。これは他の [`theme.json` 経由で追加できるスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) と同じように機能します。

<!-- 
Try this code snippet in your `theme.json` file:
 -->

このコードスニペットを、あなたの `theme.json` ファイルに試してみましょう:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/button": {
				"variations": {
					"outline": {
						"border": {
							"color": "var:preset|color|black",
							"radius": "0",
							"style": "solid",
							"width": "3px"
						},
						"shadow": "var:preset|shadow|outlined",
						"spacing": {
							"padding": {
								"top": "0.5rem",
								"bottom": "0.5rem",
								"left": "1.5rem",
								"right": "1.5rem"
							}
						}
					}
				}
			}
		}
	}
}
```

<!-- 
Feel free to adjust that and customize it to your liking. Then have fun modifying other block styles.
 -->

お好みで調整し、カスタマイズしてください。それから、他のブロック・スタイルを自由に変更して楽しんでください。

<!-- 
It is not currently possible to customize your custom-registered block styles via `theme.json`. You can only style those registered by core WordPress at the moment. For more information, check out the related [feature request on GitHub](https://github.com/WordPress/gutenberg/issues/49602).
 -->

`theme.json` 経由でカスタム登録したあなたのブロック・スタイルを、カスタマイズすることは、現在、できません。現在は、コアの WordPress で登録されたもののみをスタイル設定できます。詳細については、関連する [GitHub の機能リクエスト](https://github.com/WordPress/gutenberg/issues/49602) をご確認ください。

<!-- 
The following are the core WordPress blocks and their styles that you can customize via `theme.json`:
 -->

以下は、`theme.json` 経由でカスタマイズできる、コア WordPress ブロックとそのスタイルです:

*   **`core/button`:** `outline`, `fill`
*   **`core/image`:** `rounded`
*   **`core/quote`:** `plain`
*   **`core/site-logo`:** `rounded`
*   **`core/separator`:** `wide`, `dots`
*   **`core/social-links`:** `logos-only`, `pill-shape`
*   **`core/table`:** `stripes`
*   **`core/tag-cloud`**: `outline`

<!-- 
For a deeper dive into styling core blocks, read [Customizing core block style variations via theme.json](https://developer.wordpress.org/news/2023/02/creating-custom-block-styles-in-wordpress-themes/) on the WordPress Developer Blog.
 -->

コア・ブロックのスタイル設定についてさらに詳しく知りたい場合は、WordPress 開発者ブログの [theme.json 経由でコアのブロック・スタイル・バリエーションのカスタマイズ](https://developer.wordpress.org/news/2023/02/creating-custom-block-styles-in-wordpress-themes/) をご覧ください。.