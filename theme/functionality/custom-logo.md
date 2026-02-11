<!-- 
# Custom Logo
 -->

# カスタム・ロゴ

<!-- 
## What is a Custom Logo?
 -->

## カスタム・ロゴって ?

<!-- 
Using a custom logo allows site owners to upload an image for their website, which can be placed at the top of their website. It can be uploaded from **Appearance > Header**, in your admin panel. The custom logo support should be added first to your theme using `add_theme_support()`, and then be called in your theme using `the_custom_logo()`. A custom logo is **optional**, but theme authors should use this function if they include a logo to their theme.
 -->

カスタム・ロゴを使用すると、サイト所有者は自身の Web サイト用に画像をアップロードでき、自身の Web サイトの上部に配置できます。あなたの管理パネルの **外観 > ヘッダー** からアップロードできます。カスタム・ロゴ・サポートは、まず `add_theme_support()` を使用してあなたのテーマに追加し、その後 `the_custom_logo()` を使用してあなたのテーマ内でコールする必要があります。カスタム・ロゴは **任意** ですが、テーマ作者は、自身のテーマにロゴを含める場合、この関数を使用する必要があります。

<!-- 
### Adding Custom Logo support to your Theme
 -->

### あなたのテーマに、カスタム・ロゴ・サポートの追加

<!-- 
To enable the use of a custom logo in your theme, add the following to your `functions.php` file:
 -->

あなたのテーマでカスタム・ロゴを使用できるようにするには、あなたの `functions.php` ファイルに以下を追加しましょう:

```php
add_theme_support( 'custom-logo' );
```

<!-- 
When enabling custom logo support, you can configure five parameters by passing along arguments to the `add_theme_support()` function using an array:
 -->

カスタム・ロゴ・サポートを有効化する際、配列を使用して `add_theme_support()` 関数に引数を渡すことで、5つのパラメータを設定できます:

```php
function themename_custom_logo_setup() {
	$defaults = array(
		'height'               => 100,
		'width'                => 400,
		'flex-height'          => true,
		'flex-width'           => true,
		'header-text'          => array( 'site-title', 'site-description' ),
		'unlink-homepage-logo' => true, 
	);
	add_theme_support( 'custom-logo', $defaults );
}
add_action( 'after_setup_theme', 'themename_custom_logo_setup' );
```

<!-- 
The [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that the custom logo support is registered after the theme has loaded.
 -->

[`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) フックを使用することで、カスタム・ロゴ・サポートがテーマのロード後に登録されるようにしています。

<!-- 
*   `height`  
    Expected logo height in pixels. A custom logo can also use built-in image sizes, such as `thumbnail`, or register a custom size using [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/).
*   `width   `Expected logo width in pixels. A custom logo can also use built-in image sizes, such as `thumbnail`, or register a custom size using [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/).
*   `flex-height`  
    Whether to allow for a flexible height.
*   `flex-width   `Whether to allow for a flexible width.
*   `header-text   `Classes(s) of elements to hide. It can pass an array of class names here for all elements constituting header text that could be replaced by a logo.
*   `unlink-homepage-logo`  
    *If the `[unlink-homepage-logo](https://make.wordpress.org/core/2020/07/28/themes-changes-related-to-get_custom_logo-in-wordpress-5-5/)` parameter is set to true,* logo images inserted using `get_custom_logo()` or `the_custom_logo()` will no longer link to the homepage when visitors are on that page. In an effort to maintain the styling given to the linked image, the unlinked logo image is inside a `span` tag with the same “custom-logo-link” class.
 -->

*   `height`: ロゴの高さを、ピクセル単位で指定します。カスタム・ロゴは、`thumbnail` などのビルトイン画像サイズを使用したり、または [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/) を使用したカスタム・サイズを登録できます。
*   `width`: ロゴの幅を、ピクセル単位で指定します。カスタムロゴは、`thumbnail` などのビルトイン画像サイズを使用したり、または [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/) を使用したカスタム・サイズを登録できます。
*   `flex-height`: フレキシブルな高さを許可するか否か。
*   `flex-width`: フレキシブルな幅を許可するか否か。
*   `header-text`: 非表示にする要素のクラス名です。ロゴに置き換えられるヘッダー・テキストを構成する全要素のクラス名を、ここで配列として渡すことができます。
*   `unlink-homepage-logo`: *[`unlink-homepage-logo`](https://make.wordpress.org/core/2020/07/28/themes-changes-related-to-get_custom_logo-in-wordpress-5-5/) パラメータが `true` に設定されている場合*、`get_custom_logo()` または `the_custom_logo()` で挿入されたロゴ画像は、訪問者がそのページにいる場合、ホームページへのリンクを解除します。リンクされた画像のスタイルを維持するため、リンクされていないロゴ画像が、同じ `custom-logo-link` クラスを持つ `span` タグ内に配置されています。

<!-- 
### Displaying the custom logo in your theme
 -->

### あなたのテーマで、カスタム・ロゴの表示

<!-- 
A custom logo can be displayed in the theme using `` the_`custom_logo()` `` function. But it’s recommended to wrap the code in a `function_exists()` call to maintain backward compatibility with the older versions of WordPress, like this:
 -->

カスタム・ロゴは、`the_custom_logo()` 関数を使用して、テーマ内で表示できます。ただし、WordPress の古いバージョンとの下位互換性を維持するため、以下のように `function_exists()` コールでコードを囲むことを推奨します:

```php
if ( function_exists( 'the_custom_logo' ) ) {
	the_custom_logo();
}
```

<!-- 
Generally logos are added to the `header.php` file of the theme, but it can be elsewhere as well.
 -->

通常、ロゴはテーマの `header.php` ファイルに追加されますが、他の場所にある場合もあります。

<!-- 
If you want to get your current logo URL (or use your own markup) instead of the default markup, you can use the following code:
 -->

デフォルトのマークアップの代わりに、あなたの現在のロゴ URL を取得したい (または独自のマークアップを使用したい) 場合は、以下のコードを使用できます:

```php
$custom_logo_id = get_theme_mod( 'custom_logo' );
$logo = wp_get_attachment_image_src( $custom_logo_id , 'full' );
if ( has_custom_logo() ) {
	echo '<img src="' . esc_url( $logo[0] ) . '" alt="' . get_bloginfo( 'name' ) . '">';
} else {
	echo '<h1>' . get_bloginfo('name') . '</h1>';
}
```

<!-- 
### Custom logo template tags
 -->

### カスタム・ロゴ・テンプレート・タグ

<!-- 
To manage displaying a custom logo in the front-end, these three template tags can be used:
 -->

フロントエンドでのカスタム・ロゴ表示を管理するうえで、以下の3つのテンプレート・タグが使用できます:

<!-- 
*   `[get_custom_logo()](https://developer.wordpress.org/reference/functions/get_custom_logo/) -` Returns markup for a custom logo.
*   `[the_custom_logo()](https://developer.wordpress.org/reference/functions/the_custom_logo/) -` Displays markup for a custom logo.
*   `[has_custom_logo()](https://developer.wordpress.org/reference/functions/has_custom_logo/) -` Returns a boolean true/false, whether a custom logo is set or not.
 -->

*   [`get_custom_logo()`](https://developer.wordpress.org/reference/functions/get_custom_logo/) - カスタム・ロゴのマークアップを返します。
*   [`the_custom_logo()`](https://developer.wordpress.org/reference/functions/the_custom_logo/) - カスタム・ロゴのマークアップを表示します。
*   [`has_custom_logo()`](https://developer.wordpress.org/reference/functions/has_custom_logo/) - カスタム・ロゴが設定されているか否かを示す真偽値 `true`/`false` を返します。