<!-- 
# Featured Images &amp; Post Thumbnails
 -->

# アイキャッチ画像 &amp; 投稿サムネイル

<!-- 
Featured images (also sometimes called Post Thumbnails) are images that represent an individual Post, Page, or Custom Post Type. When you create your Theme, you can output the featured image in a number of different ways, on your archive page, in your header, or above a post, for example.
 -->

(しばしば「投稿サムネイル」とも呼ばれる) アイキャッチ画像は、個々の「投稿」、「ページ」、または「カスタム投稿タイプ」を表す画像です。あなたの「テーマ」を作成する際、たとえば、アイキャッチ画像を出力する方法はいくつかあり、あなたのアーカイブ・ページ、あなたのヘッダー、あるいは投稿の上部などに表示できます。

<!-- 
## Enabling Support for Featured Image
 -->

## アイキャッチ画像用のサポートの有効化

<!-- 
Themes must declare support for the Featured Image function before the Featured Image interface will appear on the Edit screen. Support is declared by putting the following in your theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/theme-basics/theme-functions/ "Theme Functions") file:
 -->

テーマは、「編集」画面に「アイキャッチ画像」インターフェースが表示される前に、「アイキャッチ画像」関数のサポートを宣言する必要があります。サポートは、あなたのテーマの [`functions.php`](https://make.wordpress.org/docs/theme-developer-handbook/theme-basics/theme-functions/ "Theme Functions") ファイルに、以下を記述することで宣言されます:

```php
add_theme_support( 'post-thumbnails' );
```

<!-- 
To enable Featured Image only for specific post types, see [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/ "Allows a theme to register its support of a certain feature...")
 -->

特定の投稿タイプのみに「アイキャッチ画像」を有効化するには、[`add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/ "Allows a theme to register its support of a certain feature...") をご覧ください。

<!-- 
## Setting a Featured Image
 -->

## アイキャッチ画像の設定

<!-- 
Once you add support for Featured Images, the Featured Image meta box will be visible on the appropriate content item’s Edit screens. If a user is unable to see it, they can enable it in their screen options.
 -->

「アイキャッチ画像」のサポートを追加すると、該当するコンテンツ項目の「編集」画面に「アイキャッチ画像」メタボックスが表示されます。ユーザーがそれを認識できない場合、画面オプションで有効化できます。

<!-- 
By default, the Featured Image meta box is displayed in the sidebar of the Edit Post and Edit Page screens.
 -->

デフォルトでは、「アイキャッチ画像」メタボックスは、「投稿編集」画面および「ページ編集」画面のサイドバーに表示されます。

<!-- 
[![devhbook-featured_image](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)
 -->

[![devhbook-featured_image](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
`[add_image_size()](https://developer.wordpress.org/reference/functions/add_image_size/ "Register a new image size")` – Register a new image size.  
`[set_post_thumbnail_size()](https://developer.wordpress.org/reference/functions/set_post_thumbnail_size/ "Registers an image size for the post thumbnail")` – Registers an image size for the post thumbnail.
 -->

[`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/ "Register a new image size") – 新規画像サイズを登録します。
[`set_post_thumbnail_size()`](https://developer.wordpress.org/reference/functions/set_post_thumbnail_size/ "Registers an image size for the post thumbnail") – 投稿サムネイル用の画像サイズを登録します。

<!-- 
`[has_post_thumbnail()](https://developer.wordpress.org/reference/functions/has_post_thumbnail/ "Check if post has an image attached")` – Check if post has an image attached.  
`[the_post_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail")` – Display Post Thumbnail.
 -->

[`has_post_thumbnail()`](https://developer.wordpress.org/reference/functions/has_post_thumbnail/ "Check if post has an image attached") – 投稿にサムネイル画像が添付されているか否かをチェックします。
[`the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail") –「投稿サムネイル」を表示します。

<!-- 
`[get_the_post_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")` – Retrieve Post Thumbnail.  
`[get_post_thumbnail_id()](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id/ "Retrieve Post Thumbnail ID")` – Retrieve Post Thumbnail ID.
 -->

[`get_the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail") –「投稿サムネイル」を取得します。  
[`get_post_thumbnail_id()`](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id/ "Retrieve Post Thumbnail ID") –「投稿サムネイル ID」を取得します。

<!-- 
## Image Sizes
 -->

## 画像サイズ

<!-- 
The default image sizes of WordPress are “Thumbnail”, “Medium”, “Large” and “Full Size” (the original size of the image you uploaded). These image sizes can be configured in the WordPress Administration Media panel under **\>Settings > Media**. You can also define your own image size by passing an array with your image dimensions:
 -->

WordPress のデフォルト画像サイズは、「サムネイル」「中」「大」「フルサイズ」(アップロードした画像の、本来のサイズ) です。これらの画像サイズは、**設定 > メディア** の WordPress 管理画面の「メディア」パネルで設定できます。あなたの画像の寸法を配列で渡すことで、独自の画像サイズも定義できます:

```php
the_post_thumbnail(); // Without parameter ->; Thumbnail
the_post_thumbnail( 'thumbnail' ); // Thumbnail (default 150px x 150px max)
the_post_thumbnail( 'medium' ); // Medium resolution (default 300px x 300px max)
the_post_thumbnail( 'medium_large' ); // Medium-large resolution (default 768px x no height limit max)
the_post_thumbnail( 'large' ); // Large resolution (default 1024px x 1024px max)
the_post_thumbnail( 'full' ); // Original image resolution (unmodified)
the_post_thumbnail( array( 100, 100 ) ); // Other resolutions (height, width)
```

<!-- 
## Add Custom Featured Image Sizes
 -->

## カスタム・アイキャッチ画像サイズの追加

<!-- 
In addition to defining image sizes individually using
 -->

以下の方法で、画像サイズを個別に定義する他にも…

```php
the_post_thumbnail( array(  ,  ) );
```

<!-- 
you can create custom featured image sizes in your theme’s functions file that can then be called in your theme’s template files.
 -->

あなたのテーマの関数ファイル内で、後であなたのテーマのテンプレート・ファイル内でコールできるカスタム・アイキャッチ画像サイズを作成できます。

```php
add_image_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)
```

<!-- 
Here is an example of how to create custom Featured Image sizes in your theme’s `functions.php` file.
 -->

以下は、あなたのテーマの `functions.php` ファイル内で、カスタム「アイキャッチ画像」サイズを作成する方法の例です。

```php
if ( function_exists( 'add_theme_support' ) ) {
    add_theme_support( 'post-thumbnails' );
    set_post_thumbnail_size( 150, 150, true ); // default Featured Image dimensions (cropped)

    // additional image sizes
    // delete the next line if you do not need additional image sizes
    add_image_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)
}
```

<!-- 
## Set the Featured Image Output Size
 -->

## アイキャッチ画像の、出力サイズの設定

<!-- 
To be used in the current Theme’s functions.php file.  
You can use `set_post_thumbnail_size()` to set the default Featured Image size by resizing the image proportionally (that is, without distorting it):
 -->

現在のテーマの `functions.php` ファイルで使用してください。
`set_post_thumbnail_size()` を使用すると、比率を保ったまま (つまり、歪ませずに) 画像をリサイズすることで、デフォルトの注目画像サイズを設定できます:

```php
set_post_thumbnail_size( 50, 50 ); // 50 pixels wide by 50 pixels tall, resize mode
```

<!-- 
Set the default Featured Image size by cropping the image (either from the sides, or from the top and bottom):
 -->

画像を (左右または上下から) クロップすることで、デフォルトのアイキャッチ画像サイズを設定します:

```php
set_post_thumbnail_size( 50, 50, true ); // 50 pixels wide by 50 pixels tall, crop mode
```

<!-- 
## Styling Featured Images
 -->

## アイキャッチ画像のスタイリング

<!-- 
Featured Images are given a class “wp-post-image”. They also get a class depending on the size of the thumbnail being displayed. You can style the output with these CSS selectors:
 -->

アイキャッチ画像には、`wp-post-image` クラスが付与されます。表示されるサムネイルのサイズに依存したクラスも、付与されます。以下の CSS セレクタで、出力をスタイリングできます:

```css
img.wp-post-image
img.attachment-thumbnail
img.attachment-medium
img.attachment-large
img.attachment-full
```

<!-- 
You can also give Featured Images their own classes by using the attribute parameter in [the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail").  
Display the Featured Image with a class “alignleft”:
 -->

[`the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail") の属性パラメータを使用することで、「アイキャッチ画像」に独自のクラスを割り当てることもできます。
以下では、クラス `alignleft` を付与した「アイキャッチ画像」を表示します:

```php
the_post_thumbnail( 'thumbnail', array( 'class' => 'alignleft' ) );
```

<!-- 
## Examples
 -->

## 例

<!-- 
### Default Usage
 -->

### デフォルト用法

```php
// check if the post or page has a Featured Image assigned to it.
if ( has_post_thumbnail() ) {
    the_post_thumbnail();
}
```

<!-- 
To return the Featured Image for use in your PHP code instead of displaying it, use: [get\_the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")
 -->

あなたの PHP コード内で、表示ではなく、使用するために「アイキャッチ画像」を取得するには、以下を使用します: [`get_the_post_thumbnail()`](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")

```php
// check for a Featured Image and then assign it to a PHP variable for later use
if ( has_post_thumbnail() ) {
    $featured_image = get_the_post_thumbnail();
}
```

<!-- 
### Linking to Post Permalink or Larger Image
 -->

### 投稿パーマリンクまたは大きな画像へのリンク

<!-- 
Don’t use these two examples together in the same Theme.
 -->

これらの2つの例を、同じ「テーマ」で一緒に使用しないでください。

<!-- 
Example 1. To link Post Thumbnails to the Post Permalink in a specific loop, use the following within your Theme’s template files:
 -->

例1: 特定のループ内で「投稿サムネイル」を「投稿パーマリンク」にリンクするには、あなたのテーマのテンプレート・ファイル内で、以下を使用しましょう:

```php
<?php if ( has_post_thumbnail()) : ?>
    <a href="<?php the_permalink(); ?>" alt="<?php the_title_attribute(); ?>">
        <?php the_post_thumbnail(); ?>
    </a>
<?php endif; ?>
```

<!-- 
Example 2. To link **all Post Thumbnails** on your website to the Post Permalink, put this in the current Theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/theme-functions/ "Theme Functions") file:
 -->

例2: あなたの Web サイト上の **すべての「投稿サムネイル」** を「投稿パーマリンク」にリンクするには、現在の「テーマ」の [`functions.php`](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/theme-functions/ "Theme Functions") ファイルに以下を追加しましょう:

```php
add_filter( 'post_thumbnail_html', 'my_post_image_html', 10, 3 );
function my_post_image_html( $html, $post_id, $post_image_id ) {

  $html = '<a href="' . get_permalink( $post_id ) . '">' . $html . '</a>';
  return $html;

}
```

<!-- 
This example links to the “large” Post Thumbnail image size and must be used within The Loop.
 -->

本例は「large」サイズの「投稿サムネイル」画像にリンクしており、「ループ」内で使用する必要があります。

```php
if ( has_post_thumbnail()) {
    $large_image_url = wp_get_attachment_image_src( get_post_thumbnail_id(), 'large');
    echo '<a href="' . $large_image_url[0] . '">';
    the_post_thumbnail('thumbnail');
    echo '</a>';
}
```

<!-- 
## Source File
 -->

## ソース・ファイル

<!-- 
*   [wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/tags/3.5.1/wp-includes/post-thumbnail-template.php#L0)
 -->

*   [wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/tags/3.5.1/wp-includes/post-thumbnail-template.php#L0)

<!-- 
## External Resources
 -->

## 外部リソース

<!-- 
*   [Everything you need to know about WordPress 2.9’s post image feature](http://justintadlock.com/archives/2009/11/16/everything-you-need-to-know-about-wordpress-2-9s-post-image-feature)
*   [The Ultimative Guide For the\_post\_thumbnail In WordPress 2.9](http://wpengineer.com/the-ultimative-guide-for-the_post_thumbnail-in-wordpress-2-9/)
*   [New in WordPress 2.9: Post Thumbnail Images](http://markjaquith.wordpress.com/2009/12/23/new-in-wordpress-2-9-post-thumbnail-images/)
 -->

*   [WordPress v2.9の投稿画像機能について、知っておくべきすべて](http://justintadlock.com/archives/2009/11/16/everything-you-need-to-know-about-wordpress-2-9s-post-image-feature)
*   [WordPress v2.9における、`the_post_thumbnail` の究極ガイド](http://wpengineer.com/the-ultimative-guide-for-the_post_thumbnail-in-wordpress-2-9/)
*   [WordPress v2.9の新機能: 投稿サムネイル画像](http://markjaquith.wordpress.com/2009/12/23/new-in-wordpress-2-9-post-thumbnail-images/)