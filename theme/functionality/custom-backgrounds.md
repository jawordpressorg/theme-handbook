<!-- 
# Custom Backgrounds
 -->

# カスタム背景

<!-- 
Custom Backgrounds is a theme feature that provides for customization of the background color and image.  
Theme developer needs 2 steps to implement it.
 -->

「カスタム背景」とは、背景色と背景画像のカスタマイズを可能にする、テーマ機能です。テーマ開発者は、これを実装するために2つの手順が必要です。

<!-- 
1.  Enable Custom Background – [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)
2.  Display Custom Background – [wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) and [body\_class()](https://developer.wordpress.org/reference/functions/body_class/)
 -->

1.  「カスタム背景」の有効化 – [`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/)
2.  「カスタム背景」の表示 – [`wp_head()`](https://developer.wordpress.org/reference/functions/wp_head/) および [`body_class()`](https://developer.wordpress.org/reference/functions/body_class/)

<!-- 
## Enable Custom Backgrounds
 -->

## 「カスタム背景」の有効化

<!-- 
Use [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) in the `functions.php` file to enable custom backgrounds.
 -->

カスタム背景を有効にするには、`functions.php` ファイル内で [`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) を使用します。

```php
add_theme_support( 'custom-background' );
```

<!-- 
You can specify default parameters. In below example using default ‘#0000ff’ background color (blue) with ‘wapuu.jpg’ background image that was stored under the /images folder.
 -->

デフォルトのパラメータを指定できます。以下の例では、`/images` フォルダーに保存された背景画像 `wapuu.jpg` と、デフォルトの背景色 `#0000ff` (青) を使用しています。

```php
$args = array(
    'default-color' => '0000ff',
    'default-image' => get_template_directory_uri() . '/images/wapuu.jpg',
);
add_theme_support( 'custom-background', $args );
```

<!-- 
By calling [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) , Customizer displays ‘Background Image’ menu and ‘Background Color’ section in Colors menu.
 -->

[`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/) をコールすることで、「カスタマイザー」は「背景画像」メニューと「背景色」セクションを「カラー」メニュー内に表示します。

<!-- 
## Display Custom Backgrounds
 -->

## 「カスタム背景」の表示

<!-- 
In general, invokes [wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) and [body\_class()](https://developer.wordpress.org/reference/functions/body_class/) in `header.php` file to display the custom backgrounds.
 -->

一般的に、カスタム背景を表示するには、`header.php` ファイル内で [`wp_head()`](https://developer.wordpress.org/reference/functions/wp_head/) と [`body_class()`](https://developer.wordpress.org/reference/functions/body_class/) を起動します。

```php
<!DOCTYPE html>
<html>
<head>
    <?php wp_head(); ?>
</head>
<body <?php body_class(); ?>>
```

<!-- 
[wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) generates an extra style sheet in-line with the HTML headers, usually right before the end of the document’s HEAD element. The extra style sheet overrides the background values from the theme’s style sheet.  
In our example, following code will be generated in the HTML. Notice that body tag includes “custom-background ” class.
 -->

[`wp_head()`](https://developer.wordpress.org/reference/functions/wp_head/) は、HTML ヘッダー内にインラインで追加のスタイルシートを生成し、通常はドキュメントの HEAD 要素の終了直前に配置されます。この追加のスタイルシートは、テーマのスタイルシート由来の背景値をオーバーライドします。本例では、以下のコードが HTML に生成されます。`body` タグに「custom-background」クラスが含まれていることに注意しましょう。

```php
<!DOCTYPE html>
<html lang="en-US" class="no-js">

<head>
	...
<style type="text/css" id="custom-background-css">
body.custom-background {
  background-image: url("http://example.com/wordpress/wp-content/themes/my-first-theme/images/wapuu.jpg");
  background-position: left top;
  background-size: auto;
  background-repeat: repeat;
  background-attachment: scroll;
}
</style>
	...
</head>

<body class="home page-template-default page page-id-211 logged-in admin-bar no-customize-support custom-background">

	...
```

<!-- 
Now you’ll see repeated background images
 -->

さあ、背景画像が繰り返し表示されるのが、確認できるでしょう。

<!-- 
![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_1.jpg?resize=733%2C302&ssl=1)
 -->

![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_1.jpg?resize=733%2C302&ssl=1)

<!-- 
## Another default example
 -->

## もう一つのデフォルト例

<!-- 
This is another example of default value set.
 -->

これはデフォルト値が設定された、もう一つの例です。

```php
$another_args = array(
    'default-color'      => '0000ff',
    'default-image'      => get_template_directory_uri() . '/images/wapuu.jpg',
    'default-position-x' => 'right',
    'default-position-y' => 'top',
    'default-repeat'     => 'no-repeat',
);
add_theme_support( 'custom-background', $another_args );
```

<!-- 
This will show single image at the top right corner as below.
 -->

これにより、下図のように右上隅に、一つの画像が表示されます。

<!-- 
![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_2.jpg?resize=735%2C310&ssl=1)
 -->

![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_2.jpg?resize=735%2C310&ssl=1)

<!-- 
Even if we specified the ‘default-color’ as ‘#0000ff’ (blue), the background color is not blue. Setting the default-image parameter will instantly cause that value to become the effective Custom Background, whereas setting the default-color has no effect. It is just set as default background color in Color menu of Customizer, and enhanced when Administrator save it.
 -->

たとえ「default-color」を `#0000ff` (青) に指定しても、背景色は青になりません。`default-image` パラメータを設定すると、その値が即座に有効な「カスタム背景」として反映されますが、`default-color` を設定しても効果はありません。これは「カスタマイザー」の「カラー」メニューでデフォルトの背景色として設定されるだけで、管理者が保存した時点で強化されます。

<!-- 
![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_3.jpg?resize=520%2C486&ssl=1)
 -->

![](https://i0.wp.com/developer.wordpress.org/files/2017/03/custom_background_3.jpg?resize=520%2C486&ssl=1)