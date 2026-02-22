<!-- 
# Custom Headers
 -->

# 「カスタム・ヘッダー」

<!-- 
## Custom Header
 -->

## カスタム・ヘッダー

<!-- 
[Custom headers](https://developer.wordpress.org/themes/functionality/custom-headers/) allow site owners to upload their own “title” image to their site, which can be placed at the top of certain pages. These can be customized and cropped by the user through a visual editor in the **Appearance > Header** section of the admin panel. You may also place text beneath or on top of the header. To support fluid layouts and responsive design, these headers may also be flexible. Headers are placed into a theme using `get_custom_header()`, but they must first be added to your *functions.php* file using `add_theme_support()`. Custom headers are **optional.**
 -->

[「カスタム・ヘッダー」](https://developer.wordpress.org/themes/functionality/custom-headers/) を使用すると、サイト所有者は独自の「タイトル」画像をアップロードでき、特定のページの上部に配置できます。管理パネルの **外観 > ヘッダー** セクション内のビジュアル・エディターを通じて、ユーザーがカスタマイズやトリミング可能です。ヘッダーの下部または上部に、テキストも配置できます。フルード・レイアウトとレスポンシブ・デザインをサポートするため、これらのヘッダーはフレキシブルなものにもなります。ヘッダーは `get_custom_header()` を使用してテーマに配置されますが、事前に `add_theme_support()` を用いて、あなたの *functions.php* ファイルに追加する必要があります。カスタム・ヘッダーは、**任意** です。

<!-- 
To set up a basic, flexible, custom header with text you would include the following code:
 -->

基本的なヘッダー、フレキシブル・ヘッダー、テキスト付きカスタム・ヘッダーを設定するには、以下のコードをインクルードします:

```php
<?php
function themename_custom_header_setup() {
	$args = array(
		'default-image'      => get_template_directory_uri() . 'img/default-image.jpg',
		'default-text-color' => '000',
		'width'              => 1000,
		'height'             => 250,
		'flex-width'         => true,
		'flex-height'        => true,
	);
	add_theme_support( 'custom-header', $args );
}
add_action( 'after_setup_theme', 'themename_custom_header_setup' );
```

<!-- 
 *The [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that custom headers are registered after the theme is loaded.*
 -->

*[`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) フックは、テーマがロードされた後に、カスタム・ヘッダーを登録するために使用されます。*

<!-- 
### What are Custom Headers?
 -->

### 「カスタム・ヘッダー」って ?

<!-- 
When you enable Custom Headers in your theme, users can change their header image using the WordPress theme Customizer. This gives users more control and flexibility over the look of their site.
 -->

あなたのテーマで「カスタム・ヘッダー」を有効化すると、ユーザーは WordPress テーマ・カスタマイザーを使用して、自身のヘッダー画像を変更できます。これにより、ユーザーは自身のサイトのルックについて、より多くのコントロールと柔軟性を得られます。

<!-- 
## Add Custom Header Support to your Theme
 -->

## あなたのテーマに、カスタム・ヘッダー・サポートの追加

<!-- 
To enable Custom Headers in your theme, add the following to your *`functions.php`* file:
 -->

あなたのテーマで「カスタム・ヘッダー」を有効化するには、*`functions.php`* ファイルに以下を追加しましょう:

```php
add_theme_support( 'custom-header' );
```

<!-- 
When enabling Custom Headers, you can configure several other options by passing along arguments to the `add_theme_support()` function.
 -->

「カスタム・ヘッダー」を有効化する際、`add_theme_support()` 関数に引数を渡すことで、いくつか他のオプションを設定できます。

<!-- 
You can pass specific configuration options to the `add_theme_support` function using an array:
 -->

`add_theme_support` 関数には、配列を使用して、特定の設定オプションを渡すことができます:

```php
<?php
function themename_custom_header_setup() {
	$defaults = array(
		// Default Header Image to display.
		'default-image'          => get_template_directory_uri() . '/images/headers/default.jpg',
		// Display the header text along with the image.
		'header-text'            => false,
		// Header text color default.
		'default-text-color'     => '000',
		// Header image width (in pixels).
		'width'                  => 1000,
		// Header image height (in pixels).
		'height'                 => 198,
		// Header image random rotation default.
		'random-default'         => false,
		// Enable upload of image file in admin.
		'uploads'                => false,
		// Function to be called in theme head section.
		'wp-head-callback'       => 'wphead_cb',
		// Function to be called in preview page head section.
		'admin-head-callback'    => 'adminhead_cb',
		// Function to produce preview markup in the admin screen.
		'admin-preview-callback' => 'adminpreview_cb',
	);
}
add_action( 'after_setup_theme', 'themename_custom_header_setup' );
```

<!-- 
### Flexible Header Image
 -->

### フレキシブル・ヘッダー画像

<!-- 
If flex-height or flex-width are not included in the array, height and width will be fixed sizes. If flex-height and flex-width are included, height and width will be used as suggested dimensions instead.
 -->

`flex-height` または `flex-width` が配列に含まれていない場合、高さと幅は固定サイズになります。`flex-height` と `flex-width` が含まれている場合、高さと幅は代わりに推奨寸法として使用されます。

<!-- 
### Header text
 -->

### ヘッダー・テキスト

<!-- 
By default, the user will have the option of whether or not to display header text over the image. There is no option to force the header text on the user, but if you want to remove the header text completely, you can set ‘header-text’ to ‘false’ in the arguments. This will remove the header text and the option to toggle it.
 -->

デフォルトでは、ユーザーは画像上にヘッダー・テキストを表示するか否かのオプションを有します。ヘッダー・テキストをユーザーに強制するオプションはありませんが、ヘッダー・テキストを完全に削除したい場合は、引数で `header-text` を `false` にセットできます。これによりヘッダー・テキストと、それを切り替るオプションが削除されます。

<!-- 
## Examples
 -->

## 例

<!-- 
### Set a custom header image
 -->

### カスタム・ヘッダー画像の設定

<!-- 
When the user first installs your theme, you can include a default header that will be selected before they choose their own header. This allows users to set up your theme more quickly and use your default image until they’re ready to upload their own.
 -->

ユーザーがあなたのテーマを初めてインストールした際、ユーザーが独自のヘッダーを選択する前に、選択されるデフォルト・ヘッダーをインクルードできます。これにより、ユーザーは独自の画像をアップロードする準備が整うまで、ユーザーはあなたのテーマをより迅速にセットアップし、あなたのデフォルト画像を使用できます。

<!-- 
Set a default header image 980px width and 60px height:
 -->

デフォルト・ヘッダー画像の幅を `980px`、高さを `60px` に設定します:

```php
<?php
$header_info = array(
	'width'         => 980,
	'height'        => 60,
	'default-image' => get_template_directory_uri() . '/images/sunset.jpg',
);
add_theme_support( 'custom-header', $header_info );

$header_images = array(
	'sunset' => array(
		'url'           => get_template_directory_uri() . '/images/sunset.jpg',
		'thumbnail_url' => get_template_directory_uri() . '/images/sunset_thumbnail.jpg',
		'description'   => 'Sunset',
	),
	'flower' => array(
		'url'           => get_template_directory_uri() . '/images/flower.jpg',
		'thumbnail_url' => get_template_directory_uri() . '/images/flower_thumbnail.jpg',
		'description'   => 'Flower',
	),
);
register_default_headers( $header_images );
```

<!-- 
![](https://i0.wp.com/developer.wordpress.org/files/2014/10/custom_headers_example1.jpg?resize=393%2C712&ssl=1)
 -->

![](https://i0.wp.com/developer.wordpress.org/files/2014/10/custom_headers_example1.jpg?resize=393%2C712&ssl=1)

<!-- 
Do not forget to call [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) to register a default image. In this example, `sunset.jpg` is the default image and `flower.jpg` is an alternative selection in Customizer.
 -->

デフォルト画像を登録するには、[`register_default_headers()`](https://developer.wordpress.org/reference/functions/register_default_headers/) をコールすることを忘れないでください。本例では、`sunset.jpg` がデフォルト画像であり、`flower.jpg` は、「カスタマイザー」での代替選択肢です。

<!-- 
From Administration Screen, Click **Appearance > Header** to display Header Image menu in Customizer. Notice that width and height specified in [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) is displayed as recommended size, and `flower.jpg` is shown as selectable option.
 -->

管理画面から、**外観 > ヘッダー** をクリックすると、「カスタマイザー」にヘッダー画像メニューが表示されます。[`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) で指定した幅と高さが推奨サイズとして表示され、`flower.jpg` が選択可能なオプションとして表示されることに注意してください。

<!-- 
### Use flexible headers
 -->

### フレキシブル・ヘッダーの使用

<!-- 
By default, the user will have to crop any images they upload to fit in the width and height you specify. However, you can let users upload images of any height and width by specifying ‘flex-width’ and ‘flex-height’ as true. This will let the user skip the cropping step when they upload a new photo.
 -->

デフォルトでは、ユーザーはアップロードする画像を、指定した幅と高さに合わせて、クロップする必要があります。ただし、`flex-width` と `flex-height` を `true` として指定することで、ユーザーは任意の高さと幅の画像をアップロードできます。これにより、ユーザーが新規写真をアップロードする際、クロップ工程をスキップできます。

<!-- 
Set flexible headers:
 -->

フレキシブル・ヘッダーを設定し:

```php
<?php
$args = array(
	'flex-width'    => true,
	'width'         => 980,
	'flex-height'   => true,
	'height'        => 200,
	'default-image' => get_template_directory_uri() . '/images/header.jpg',
);
add_theme_support( 'custom-header', $args );
```

<!-- 
update your `header.php` file to:
 -->

あなたの `header.php` ファイルを、以下のようにアップデートしましょう:

```php
<img alt="" src="<?php header_image(); ?>" width="<?php echo absint( get_custom_header()->width ); ?>" height="<?php echo absint( get_custom_header()->height ); ?>">
```

<!-- 
### Displaying Custom Header
 -->

### カスタム・ヘッダーの表示

<!-- 
To display the custom header, function [get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) retrieves the header image. [get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) gets the custom header data.  
E.g. below shows how custom header images can be used to display the header in the theme. The below code goes into header.php file.
 -->

カスタム・ヘッダーを表示するには、関数 [`get_header_image()`](https://developer.wordpress.org/reference/functions/get_header_image/) がヘッダー画像を取得します。[`get_custom_header()`](https://developer.wordpress.org/reference/functions/get_custom_header/) は、カスタム・ヘッダー・データを取得します。
たとえば、以下は、テーマ内でヘッダーを表示するためにカスタム・ヘッダー画像を使用する方法を示しています。以下のコードを `header.php` ファイルに記述します。

```php
<?php if ( get_header_image() ) : ?>
	<div id="site-header">
		<a href="<?php echo esc_url( home_url( '/' ) ); ?>" rel="home">
			<img src="<?php header_image(); ?>" width="<?php echo absint( get_custom_header()->width ); ?>" height="<?php echo absint( get_custom_header()->height ); ?>" alt="<?php echo esc_attr( get_bloginfo( 'name', 'display' ) ); ?>">
		</a>
	</div>
<?php endif; ?>
```

<!-- 
### Backwards Compatibility
 -->

### 下位互換性

<!-- 
Custom Headers are supported in WordPress 3.4 and above. If you’d like your theme to support WordPress installations that are older than 3.4, you can use the following code instead of `add_theme_support( ‘custom-header’);`
 -->

「カスタム・ヘッダー」は、WordPress v3.4以降でサポートされています。あなたのテーマで v3.4より古い WordPress インストールをサポートしたい場合は、`add_theme_support( ‘custom-header’)` の代わりに、以下のコードを使用できます;

```php
<?php
global $wp_version;
if ( version_compare( $wp_version, '3.4', '>=' ) ) :
	add_theme_support( 'custom-header' );
else :
	add_custom_image_header( $wp_head_callback, $admin_head_callback );
endif;
```

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
*   [header\_image()](https://developer.wordpress.org/reference/functions/header_image/) Display header image URL.
*   [get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) Retrieve header image for custom header.
*   [get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) Get the header image data.
*   [get\_random\_header\_image()](https://developer.wordpress.org/reference/functions/get_random_header_image/) Retrieve header image for custom header.
*   [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) Registers theme support for a given feature.
*   [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) Registers a selection of default headers to be displayed by the Customizer.
 -->

*   [`header_image()`](https://developer.wordpress.org/reference/functions/header_image/) ヘッダー画像の URL を表示します。
*   [`get_header_image()`](https://developer.wordpress.org/reference/functions/get_header_image/) カスタム・ヘッダー用のヘッダー画像を取得します。
*   [`get_custom_header()`](https://developer.wordpress.org/reference/functions/get_custom_header/) ヘッダー画像データを取得します。
*   [`get_random_header_image()`](https://developer.wordpress.org/reference/functions/get_random_header_image/) カスタム・ヘッダー用のヘッダー画像を取得します。
*   [`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) 指定された機能に関する、テーマ・サポートを登録します。
*   [`register_default_headers()`](https://developer.wordpress.org/reference/functions/register_default_headers/) 「カスタマイザー」で表示される、デフォルト・ヘッダーの選択肢を登録します。