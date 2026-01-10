<!-- 
# Theme Functions
 -->

# テーマ関数

<!-- 
`Functions.php` can be used by both classic themes, block themes, and child themes.
 -->

`functions.php` は、クラシック・テーマ、ブロック・テーマ、子テーマのいずれでも使用できます。

<!-- 
The `functions.php` file is where you add unique features to your WordPress theme. It can be used to hook into the core functions of WordPress to make your theme more modular, extensible, and functional.
 -->

`functions.php` ファイルは、あなたの WordPress テーマに、独自の機能を追加する場所です。これにより、WordPress のコア機能にフックして、あなたのテーマをよりモジュール化し、拡張性を持たせ、機能的なものにできます。

<!-- 
## What is `functions.php`?
 -->

## `functions.php` って ?

<!-- 
The `functions.php` file behaves like a WordPress plugin, adding features and functionality to a WordPress site. You can use it to call WordPress functions and to define your own functions.
 -->

`functions.php` ファイルは、WordPress プラグインのように動作し、WordPress サイトに機能や操作性を追加します。これにより、WordPress 関数をコールしたり、独自の関数を定義したりできます。

<!-- 
The same result can be produced using either a plugin or `functions.php`. If you are creating new features that should be available no matter what the website looks like, **it is best practice to put them in a plugin**.
 -->

プラグインと `functions.php` のどちらを使用しても、同じ結果を得られます。Web サイトの見た目にかかわらず、常に利用可能な新機能を作成する場合は、**プラグインに実装するのが、ベスト・プラクティスです**。

<!-- 
There are advantages and tradeoffs to either using a WordPress plugin or using `functions.php`.
 -->

WordPress プラグインを使用する場合と `functions.php` を使用する場合とでは、それぞれ利点とトレードオフがあります。

<!-- 
A WordPress plugin:
 -->

WordPress プラグインでは:

<!-- 
*   requires specific, unique header text;
*   is stored in wp-content/plugins, usually in a subdirectory;
*   only executes on page load when activated;
*   applies to all themes; and
*   should have a single purpose – for example, offer search engine optimization features or help with backups.
 -->

*   特定の一意なヘッダー・テキストが必要です;
*   `wp-content/plugins` 内の、通常はサブディレクトリ内に、保存されます;
*   有効化されている場合、ページ・ロード時にのみ実行されます;
*   すべてのテーマに適用されます; そして
*   単一の目的 – たとえば、SEO (検索エンジン最適化) 機能を提供したり、バックアップを支援したり – を持つべきです。

<!-- 
Meanwhile, a `functions.php` file:
 -->

一方、`functions.php` ファイルでは:

<!-- 
*   requires no unique header text;
*   is stored in theme’s subdirectory in wp-content/themes;
*   executes only when in the active theme’s directory;
*   applies only to that theme (if the theme is changed, the features can no longer be used); and
*   can have numerous blocks of code used for many different purposes.
 -->

*   独自のヘッダー・テキストを必要としません;
*   `wp-content/themes` 内の、テーマのサブディレクトリ内に、保存されます;
*   有効化されたテーマのディレクトリ内でのみ、実行されます;
*   そのテーマにのみ適用され (テーマを変更すると、その機能は使用できない) ます; そして
*   さまざまな目的で使用される、多数のコード・ブロックを持つことができます。

<!-- 
Each theme has its own functions file, but only code in the active theme’s `functions.php` is actually run. If your theme already has a functions file, you can add code to it. If not, you can create a plain-text file named `functions.php` to add to your theme’s directory, as explained below.
 -->

各テーマには独自の関数ファイルがありますが、実際に実行されるのは、有効化されているテーマの `functions.php` 内のコードのみです。あなたのテーマにすでに関数ファイルがある場合は、そこにコードを追加できます。ない場合は、下記で説明するとおり、あなたのテーマのディレクトリに `functions.php` という名前のプレーン・テキストファイルを作成して追加できます。

<!-- 
A [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/) can have its own `functions.php` file. Adding a function to the child functions file is a risk-free way to modify a parent theme. That way, when the parent theme is updated, you don’t have to worry about your newly added function disappearing.
 -->

[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) は、独自の `functions.php` ファイルを持つことができます。子テーマの関数ファイルに関数を追加することは、親テーマを変更するリスクのない方法です。そうすることで、親テーマが更新されても、あなたが新しく追加した関数が消えてしまう心配はありません。

<!-- 
Although the child theme’s `functions.php` is loaded by WordPress right before the parent theme’s `functions.php`, it does not *override* it. The child theme’s `functions.php` can be used to augment or replace the parent theme’s functions. Similarly, `functions.php` is loaded *after any plugin files have loaded*.
 -->

子テーマの `functions.php` は、親テーマの `functions.php` の直前に、WordPress によってロードされますが、それを *上書き* することはありません。子テーマの `functions.php` は、親テーマの機能を拡張または置換するために使用できます。同様に、`functions.php` は *任意のプラグイン・ファイルがロードされた後* に、ロードされます。

<!-- 
With `functions.php` you can:
 -->

`functions.php` を使用すると、次のことが可能になります:

<!-- 
*   Use WordPress hooks. For example, with [the `excerpt_length`](https://developer.wordpress.org/reference/hooks/excerpt_length/) filter you can change your post excerpt length (from default of 55 words).
*   Enable WordPress features with `[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)`. For example, turn on post thumbnails, post formats, and navigation menus.
*   Define functions you wish to reuse in multiple theme template files.
 -->

*   WordPress フックを使用する。たとえば、with [the `excerpt_length`](https://developer.wordpress.org/reference/hooks/excerpt_length/) フィルターで、あなたの投稿の抜粋長を (デフォルトの55語から) 変更できます。
*   `[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)` で WordPress 機能を有効化する。たとえば、投稿サムネイル、投稿フォーマット、ナビゲーション・メニューを有効化します。
*   複数のテーマ・テンプレート・ファイルで再利用したい関数を、定義します。

<!-- 
In WordPress, naming conflicts can occur when two or more functions, classes, or variables have the same name. This can cause errors or unexpected behavior in a WordPress site. It is the responsibility of both the theme developer and plugin developer to avoid naming conflicts in their respective code.
 -->

WordPress では、2つ以上の関数、クラス、または変数が同じ名称である場合に名称衝突が発生する可能性があります。これにより、WordPress サイトでエラーや予期しない挙動が引き起こされることがあります。テーマ開発者とプラグイン開発者の双方が、それぞれのコード内で、名称衝突を回避する責任を負います。

<!-- 
Theme developers should ensure that their functions, classes, and variables have unique names that do not conflict with those used by WordPress core or other plugins. They should also prefix their function and class names with a unique identifier, such as the theme name or abbreviation, to minimize the chances of a naming conflict.
 -->

テーマ開発者は、自身の関数、クラス、変数が WordPress コアや他のプラグインで使用されているものと衝突しない、一意の名称であることを確認する必要があります。また、名称衝突の可能性を最小限に抑えるため、関数名やクラス名には、テーマ名や略称など、一意の識別子を接頭辞として付けるべきです。

<!-- 
## Examples
 -->

## 例

<!-- 
Below are a number of examples that you can use in your functions.php file to support various features. Each of these examples are allowed in your theme if you choose to submit it to the WordPress.org theme directory.
 -->

以下に、さまざまな機能をサポートするために、あなたの functions.php ファイルで使用できる、いくつかの例を示します。これらの例はいずれも、WordPress.org テーマ・ディレクトリに提出することを選択した場合、あなたのテーマでの使用が許可されています。

<!-- 
### Theme Setup
 -->

### テーマ・セットアップ

<!-- 
A number of theme features should be included within a “setup” function that runs initially when your theme is activated. As shown below, each of these features can be added to your `functions.php` file to activate recommended WordPress features.
 -->

あなたのテーマを有効化した際に最初に実行される「セットアップ」関数には、いくつかのテーマ機能を含める必要があります。以下に示すように、これらの各機能は、推奨される WordPress 機能を有効化するために、あなたの `functions.php` ファイルに追加できます。

<!-- 
It’s important to namespace your functions with your theme name. All examples below use `myfirsttheme_` as their namespace, which should be customized based on your theme name.
 -->

あなたの関数には、あなたのテーマ名で、名前空間を付けることが重要です。以下のすべての例では名前空間として `myfirsttheme_` を使用していますが、これはあなたのテーマ名にもとづいてカスタマイズする必要があります。

<!-- 
To create this initial function, start a new function entitled `myfirsttheme_setup()`, like so:
 -->

この初期関数を作成するには、次のように、`myfirsttheme_setup()` という名称の新規関数を開始します:

```php
if ( ! function_exists( 'myfirsttheme_setup' ) ) :
/**
 * Sets up theme defaults and registers support for various WordPress  
 * features.
 *
 * It is important to set up these functions before the init hook so
 * that none of these features are lost.
 *
 *  @since MyFirstTheme 1.0
 */
function myfirsttheme_setup() { ... }
```

<!-- 
Note: In the above example, the function myfirsttheme\_setup is started but not closed out. Be sure to close out your functions.
 -->

注: 上記の例では、関数 `myfirsttheme_setup` が開始されていますが、終了されていません。あなたの関数は、必ず終了してください。

<!-- 
#### Automatic Feed Links
 -->

#### 自動フィード・リンク

<!-- 
Automatic feed links enables post and comment RSS feeds by default. These feeds will be displayed in `<head>` automatically. They can be called using `[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)` in classic themes. This feature is automatically enabled for block themes, and does not need to be included during theme setup.
 -->

自動フィードリンクにより、投稿とコメントの RSS フィードが、デフォルトで有効になります。これらのフィードは、`<head>` 内で自動的に表示されます。クラシック・テーマでは、`[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)` を使用してコールできます。ブロック・テーマでは、この機能は自動的に有効化され、テーマ・セットアップ時に含める必要はありません。

```php
add_theme_support( 'automatic-feed-links' );
```

<!-- 
#### Navigation Menus
 -->

#### ナビゲーション・メニュー

<!-- 
In classic themes, custom [navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/ "Navigation Menus") allow users to edit and customize menus in the Menus admin panel, giving users a drag-and-drop interface to edit the various menus in their theme.
 -->

クラシック・テーマでは、カスタム [ナビゲーション・メニュー](https://developer.wordpress.org/themes/functionality/navigation-menus/ "Navigation Menus") により、ユーザーは「メニュー」管理パネルで、メニューを編集およびカスタマイズでき、これにより、テーマ内の各種メニューを編集するための、ドラッグ & ドロップ・インターフェースが提供されます。

<!-- 
You can set up multiple menus in `functions.php`. They can be added using `[register_nav_menus()](https://developer.wordpress.org/reference/functions/register_nav_menus/)` and inserted into a theme using `[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)`, as discussed [later in this handbook](https://developer.wordpress.org/themes/functionality/navigation-menus/). If your theme will allow more than one menu, you should use an array. While some themes will not have custom navigation menus, it is recommended that you allow this feature for easy customization.
 -->

`functions.php` で複数のメニューをセットアップできます。[このハンドブックの後半](https://developer.wordpress.org/themes/functionality/navigation-menus/) で説明するように、これらは `[register_nav_menus()](https://developer.wordpress.org/reference/functions/register_nav_menus/)` を使用して追加し、`[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)` を使用してテーマに挿入できます。あなたのテーマが複数のメニューを許可する場合、配列を使用すべきです。カスタム・ナビゲーション・メニューがないテーマもありますが、カスタマイズを容易にするため、この機能を有効にすることをおすすめします。

```php
register_nav_menus( array(
    'primary'   => __( 'Primary Menu', 'myfirsttheme' ),
    'secondary' => __( 'Secondary Menu', 'myfirsttheme' )
) );
```

<!-- 
Each of the menus you define can be called later using `[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)` and using the name assigned (i.e. primary) as the `theme_location` parameter.
 -->

定義した各メニューは、後で `[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)` 関数を使用する際に、`theme_location` パラメータとして、割り当てた名称 (たとえば primary) を指定することで、コールできます。

<!-- 
In block themes, you use the [navigation block](https://wordpress.org/support/article/navigation-block/) instead.
 -->

ブロック・テーマでは、代わりに [ナビゲーション・ブロック](https://wordpress.org/support/article/navigation-block/) を使用します。

<!-- 
#### Load Text Domain
 -->

#### Text Domain のロード

<!-- 
Themes can be translated into multiple languages by making the strings in your theme available for translation. To do so, you must use `[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)`. For more information on making your theme available for translation, read the [internationalization](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization & Text Domains") section.
 -->

テーマは、あなたのテーマ内の文字列を翻訳可能にすることで、複数の言語に翻訳できます。その為には、`[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)` を使用する必要があります。あなたのテーマを翻訳可能にする方法の詳細については、[国際化](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization & Text Domains") セクションをご覧ください。

```php
load_theme_textdomain( 'myfirsttheme', get_template_directory() . '/languages' );
```

<!-- 
#### Post Thumbnails
 -->

#### 投稿サムネイル

<!-- 
[Post thumbnails and featured images](https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/ "Featured Images & Post Thumbnails") allow your users to choose an image to represent their post. Your theme can decide how to display them, depending on its design. For example, you may choose to display a post thumbnail with each post in an archive view. Or, you may want to use a large featured image on your homepage. This feature is automatically enabled for block themes, and does not need to be included during theme setup.
 -->

[投稿サムネイルと注目画像](https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/ "Featured Images & Post Thumbnails") は、あなたのユーザーが、自身の投稿を表す画像を選択できるようにします。あなたのテーマは、そのデザインに応じて、それらをどのように表示するかを決定できます。たとえば、アーカイブ表示の各投稿に、投稿サムネイルを表示するように選択できます。あるいは、あなたのホームページで、大きな注目画像を使用したい場合もあるでしょう。ブロック・テーマでは、この機能は自動的に有効化され、テーマ・セットアップ時に含める必要はありません。

```php
add_theme_support( 'post-thumbnails' );
```

<!-- 
#### Post Formats
 -->

#### 投稿フォーマット

<!-- 
[Post formats](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") allow users to format their posts in different ways. This is useful for allowing bloggers to choose different formats and templates based on the content of the post. `add_theme_support()` is also used for Post Formats. This is **recommended**.
 -->

[投稿フォーマット](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") は、ユーザーが自身の投稿をさまざまな方法でフォーマットすることを可能にします。これは、ブロガーが投稿のコンテンツにもとづいて、さまざまなフォーマットやテンプレートを選択できるようにするのに役立ちます。`add_theme_support()` は、「投稿フォーマット」にも使用されます。これは **推奨** されています。

```php
add_theme_support( 'post-formats',  array( 'aside', 'gallery', 'quote', 'image', 'video' ) );
```

<!-- 
[Learn more about post formats.](https://developer.wordpress.org/themes/functionality/post-formats/)
 -->

[投稿フォーマットの詳細について、学びましょう](https://developer.wordpress.org/themes/functionality/post-formats/)。

<!-- 
#### Theme support in block themes
 -->

#### ブロック・テーマでの、テーマ・サポート

<!-- 
In block themes, the following theme supports are enabled automatically:
 -->

ブロック・テーマでは、以下のテーマ・サポートが、自動的に有効化されます:

```php
add_theme_support( 'post-thumbnails' );
add_theme_support( 'responsive-embeds' );
add_theme_support( 'editor-styles' );
add_theme_support( 'html5', array( 'style','script' ) );
add_theme_support( 'automatic-feed-links' ); 
```

<!-- 
#### Initial Setup Example
 -->

#### 初期セットアップ例

<!-- 
Including all of the above features will give you a `functions.php` file like the one below. Code comments have been added for future clarity.
 -->

上記の機能をすべて含めると、以下のような `functions.php` ファイルになります。将来参照しやすいよう、コードにコメントを追加しています。

<!-- 
As shown at the bottom of this example, you must add the required `[add_action()](https://developer.wordpress.org/reference/functions/add_action/)` statement to ensure the `myfirsttheme_setup` function is loaded.
 -->

この例の末尾に示すように、`myfirsttheme_setup` 関数がロードされるように、要求される `[add_action()](https://developer.wordpress.org/reference/functions/add_action/)` 文を必ず追加してください。

```php
if ( ! function_exists( 'myfirsttheme_setup' ) ) :
	/**
	 * Sets up theme defaults and registers support for various
	 * WordPress features.
	 *
	 * Note that this function is hooked into the after_setup_theme
	 * hook, which runs before the init hook. The init hook is too late
	 * for some features, such as indicating support post thumbnails.
	 */
	function myfirsttheme_setup() {

    /**
	 * Make theme available for translation.
	 * Translations can be placed in the /languages/ directory.
	 */
		load_theme_textdomain( 'myfirsttheme', get_template_directory() . '/languages' );

		/**
		 * Add default posts and comments RSS feed links to <head>.
		 */
		add_theme_support( 'automatic-feed-links' );

		/**
		 * Enable support for post thumbnails and featured images.
		 */
		add_theme_support( 'post-thumbnails' );

		/**
		 * Add support for two custom navigation menus.
		 */
		register_nav_menus( array(
			'primary'   => __( 'Primary Menu', 'myfirsttheme' ),
			'secondary' => __( 'Secondary Menu', 'myfirsttheme' ),
		) );

		/**
		 * Enable support for the following post formats:
		 * aside, gallery, quote, image, and video
		 */
		add_theme_support( 'post-formats', array( 'aside', 'gallery', 'quote', 'image', 'video' ) );
	}
endif; // myfirsttheme_setup
add_action( 'after_setup_theme', 'myfirsttheme_setup' );
```

<!-- 
### Content Width
 -->

### コンテンツ幅

<!-- 
In classic themes, a content width is added to your `functions.php` file to ensure that no content or assets break the container of the site. The content width sets the maximum allowed width for any content added to your site, including uploaded images. In the example below, the content area has a maximum width of 800 pixels. No content will be larger than that.
 -->

クラシック・テーマでは、あなたの `functions.php` ファイルにコンテンツ幅を追加することで、コンテンツやアセットが、サイトのコンテナを崩さないようにします。コンテンツ幅は、アップロードされた画像を含む、あなたのサイトに追加される任意のコンテンツの最大許容幅を設定します。以下の例では、コンテンツ領域の最大幅は、800ピクセルです。コンテンツはこれより大きく表示されることはありません。

```php
if ( ! isset ( $content_width) ) {
    $content_width = 800;
}
```

<!-- 
Themes that include a theme.json configuration file does not need to include the variable in functions.php. Instead, the content width is added to the layout setting in theme.json. You can [learn more about using theme.json in the advanced section](https://developer.wordpress.org/themes/advanced-topics/theme-json/).
 -->

`theme.json` 設定ファイルを備えたテーマでは、`functions.php` にこの変数を記述する必要はありません。代わりに、コンテンツ幅は `theme.json` のレイアウト設定に追加されます。[`theme.json` の使用方法に関する詳細情報は、上級者向けセクションで学習](https://developer.wordpress.org/themes/advanced-topics/theme-json/) できます。

<!-- 
### Other Features
 -->

### その他の機能

<!-- 
There are other common features you can include in `functions.php`. Listed below are some of the most common features. Click through and learn more about each of these features.
 -->

`functions.php` に含めることができる、その他の一般的な機能があります。最も一般的な機能の一部を、以下に示します。各機能の詳細については、リンクをクリックしてご覧ください。

<!-- 
*   [Custom Headers](https://developer.wordpress.org/themes/functionality/custom-headers/) **\-Classic themes**
*   [Sidebars](https://developer.wordpress.org/themes/functionality/sidebars/) (widget areas) **\-Classic themes**
*   Custom Background **\-Classic themes**
*   Title tag **\-Classic themes**
*   Add Editor Styles
*   HTML5 **\-Classic themes**
 -->

*   [カスタム・ヘッダー](https://developer.wordpress.org/themes/functionality/custom-headers/) **\-クラシック・テーマ**
*   [サイドバー](https://developer.wordpress.org/themes/functionality/sidebars/) (ウィジェット・エリア) **\-クラシック・テーマ**
*   カスタム背景 **\-クラシック・テーマ**
*   タイトル・タグ **\-クラシック・テーマ**
*   エディター・スタイルの追加
*   HTML5 **\-クラシック・テーマ**

<!-- 
## Your *functions.php* File
 -->

## あなたの *functions.php* ファイル

<!-- 
If you choose to include all the functions listed above, this is what your *functions.php* might look like. It has been commented with references to above.
 -->

上記の機能をすべて含めることを選択した場合、あなたの *functions.php* は、以下のようになります。上記への参照を、コメントとして付記しています。

```php
/**
 * MyFirstTheme's functions and definitions
 *
 * @package MyFirstTheme
 * @since MyFirstTheme 1.0
 */

/**
 * First, let's set the maximum content width based on the theme's
 * design and stylesheet.
 * This will limit the width of all uploaded images and embeds.
 */
if ( ! isset( $content_width ) ) {
	$content_width = 800; /* pixels */
}


if ( ! function_exists( 'myfirsttheme_setup' ) ) :

	/**
	 * Sets up theme defaults and registers support for various
	 * WordPress features.
	 *
	 * Note that this function is hooked into the after_setup_theme
	 * hook, which runs before the init hook. The init hook is too late
	 * for some features, such as indicating support post thumbnails.
	 */
	function myfirsttheme_setup() {

		/**
		 * Make theme available for translation.
		 * Translations can be placed in the /languages/ directory.
		 */
		load_theme_textdomain( 'myfirsttheme', get_template_directory() . '/languages' );

		/**
		 * Add default posts and comments RSS feed links to <head>.
		 */
		add_theme_support( 'automatic-feed-links' );

		/**
		 * Enable support for post thumbnails and featured images.
		 */
		add_theme_support( 'post-thumbnails' );

		/**
		 * Add support for two custom navigation menus.
		 */
		register_nav_menus( array(
			'primary'   => __( 'Primary Menu', 'myfirsttheme' ),
			'secondary' => __( 'Secondary Menu', 'myfirsttheme' ),
		) );

		/**
		 * Enable support for the following post formats:
		 * aside, gallery, quote, image, and video
		 */
		add_theme_support( 'post-formats', array( 'aside', 'gallery', 'quote', 'image', 'video' ) );
	}
endif; // myfirsttheme_setup
add_action( 'after_setup_theme', 'myfirsttheme_setup' );
```