<!-- 
# Child Themes
 -->

# 子テーマ

<!-- 
Child themes are extensions of a parent theme. They allow you to modify an existing theme without directly editing that theme’s code. They are often something as simple as a few minor color changes, but they can also be complex and include custom overrides of the parent theme.
 -->

子テーマとは、親テーマの拡張です。親テーマのコードを直接編集することなく、既存のテーマを変更できます。ちょっとした色の変更など簡単なものも多いが、親テーマのカスタムオーバーライドなど複雑なものもあります。

<!-- 
In this article, you will learn what parent and child themes are, how to create your own modifications via child themes, and what pieces of a parent theme that can be overridden.
 -->

本稿では、親テーマと子テーマとは何か、子テーマを経由して独自の変更を作成する方法と、親テーマのどの部分をオーバーライドできるかを学びます。

<!-- 
## What are parent and child themes?
 -->

## 親テーマと子テーマって ?

<!-- 
### Parent themes
 -->

### 親テーマ

<!-- 
All themes—unless they are specifically a child theme—are technically parent themes. Basically, this means that they are complete themes that can be installed and activated in WordPress. 
 -->

すべてのテーマは、—特に子テーマでない限り— 技術的には親テーマです。基本的に、これは、WordPress にインストールして有効化できる完全なテーマであることを意味します。

<!-- 
Parent themes must have all of the required files, as outlined in the [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/) documentation. Beyond that, you don’t have to do anything special for your theme to *become a parent theme.*
 -->

[テーマ構造](https://developer.wordpress.org/themes/core-concepts/theme-structure/) ドキュメントで説明されているように、親テーマは、必要なファイルをすべて持っている必要があります。それ以上に、あなたのテーマが *親テーマになる* ために特別なことをする必要はありません。

<!-- 
### Child themes
 -->

### 子テーマ

<!-- 
A child theme includes everything from its parent theme by default. This includes the design and any of its functionality. But it can also be used to make customizations to the parent theme without directly modifying the parent theme’s files. This means that you (or your child theme’s users) can still receive updates to the parent theme without losing those modifications.
 -->

子テーマは、デフォルトで親テーマのすべてを含みます。これには、デザインや機能性が含まれます。しかし、親テーマのファイルを直接変更することなく、親テーマもカスタマイズできます。つまり、あなた (または子テーマのユーザー) は、それらの修正を失うことなく、親テーマのアップデートを受け取ることができます。

<!-- 
Child themes:
 -->

子テーマとは:

<!-- 
*   Make your modifications portable and replicable.
*   Keep customizations separate from the parent theme.
*   Allow parent themes to be updated without losing your modifications.
*   Save on development time since you’re only writing the code you need.
*   Are a great way to start your journey toward developing full themes.
 -->

*   あなたの修正を、移植可能で複製可能なものにします。
*   カスタマイズは、親テーマから分離します。
*   親テーマのアップデートを、あなたの修正を失うことなく行えるようにします。
*   必要なコードだけを書くので、開発時間を節約できます。
*   完全なテーマ開発への、あなたの旅を開始するのに最適な方法です。

<!-- 
It’s worth noting that making extensive customizations from within a child theme can eventually become a management headache. For these more extensive projects, it is often better to fork the original theme and create a full/parent theme of your own. This is something you will need to decide on a case-by-case basis.
 -->

子テーマの中から大規模カスタマイズを行うことは、最終的には管理の頭痛の種になる可能性があることは、注目に値します。このような大規模プロジェクトでは、オリジナルのテーマをフォークして、独自の完全な/親テーマを制作したほうが良い場合が多いです。これはケース・バイ・ケースで決める必要があります。

<!-- 
### What about grandchild themes?
 -->

### 孫テーマについては ?

<!-- 
This is not currently possible. There are only two levels to the standard theme hierarchy: parent and child theme.
 -->

現在のところ、これは不可能です。標準的なテーマの階層には2つのレベルしかありません: 親テーマと子テーマです。

<!-- 
However, when building block themes, there are other levels to what is presented on the front end of a site (they are just not a part of the theme layer):
 -->

しかし、ブロック・テーマを構築する場合、サイトのフロントエンドに表示されるものには、他のレベルがあります (それらはテーマ・レイヤーの一部ではないだけ):

<!-- 
*   WordPress itself (default `theme.json`)
*   Parent theme
*   Child theme
*   User customizations (can override `theme.json`, templates, and patterns)
 -->

*   WordPress 自身 (デフォルト `theme.json`)
*   親テーマ
*   子テーマ
*   ユーザー・カスタマイズ (`theme.json`、テンプレート、パターンをオーバーライド可能)

<!-- 
In a way, the user customization layer works as a “grandchild” theme of sorts. The big difference is that the changes are stored in the database instead of the filesystem.
 -->

ある意味、ユーザー・カスタマイズ・レイヤーは、一種の「孫」テーマとして機能します。大きな違いは、変更がファイルシステムではなくデータベースに保存されることです。

<!-- 
Outside of that, there is no standard method of creating an installable grandchild theme.
 -->

それ以外では、インストール可能な孫テーマを制作する標準的な方法はありません。

<!-- 
## How to create a child theme
 -->

## 子テーマの制作方法

<!-- 
Let’s try creating a child theme of the default [Twenty Twenty-Four](https://wordpress.org/themes/twentytwentyfour/) theme bundled with WordPress. 
 -->

WordPress にバンドルされているデフォルト・テーマ [Twenty Twenty-Four](https://wordpress.org/themes/twentytwentyfour/) を作成してみましょう。

<!-- 
### Create a child theme folder
 -->

### 子テーマフォルダーの作成

<!-- 
First, your child theme needs a name. This can be whatever you want your theme to be called, but for this guide, let’s name it “Grand Sunrise.”
 -->

まず、あなたの子テーマには名称が必要です。あなたのテーマの名称は何でもかまわないが、このガイドでは「Grand Sunrise」と名付けましょう。

<!-- 
Now create a new folder in your `wp-content/themes` directory with a kebab-case version of your theme name: `grand-sunrise`.
 -->

それでは、あなたの `wp-content/themes` ディレクトリに、あなたのテーマ名のケバブ・ケース版の新規フォルダーを作成します: `grand-sunrise`。

<!-- 
### Create a style.css
 -->

### style.css の制作

<!-- 
Now you’ll need to create a file named `style.css`. It is the one absolutely necessary file for a child theme to exist. All `style.css` files must contain a File Header and the required header fields, as outlined in the [Main Stylesheet](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/) documentation (please review this doc if you have not already done so).
 -->

次に、`style.css` という名称のファイルを制作する必要があります。子テーマが存在するために、絶対に必要なファイルです。[メイン・スタイルシート](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/) ドキュメント (未見の人は、このドキュメントをご覧あれ) で説明されているように、すべての `style.css` ファイルは、「ファイル・ヘッダー」と、必要なヘッダー・フィールドを必ず含む必要があります。

<!-- 
As noted in the Main Stylesheet documentation, there is an additional field necessary to declare a theme as a child theme. You must add the `Template` header field to the `style.css` File Header:
 -->

メイン・スタイルシートのドキュメントで述べられているように、テーマを子テーマとして宣言するには、追加のフィールドが必要です。`Template` ヘッダー・フィールドを `style.css`「ファイル・ヘッダー」に追加する必要があります:

```css
/**
 * Theme Name: Grand Sunrise
 * Template:   twentytwentyfour
 * ...other header fields
 */
```

<!-- 
There is one caveat to the `Template` field. It must be a 100% match of the folder name of the parent theme, relative to the `wp-content/themes` folder. In this case, we know that the Twenty Twenty-Four theme folder is located at `wp-content/themes/twentytwentyfour`. Therefore, the `Template` value must be `twentytwentyfour`.
 -->

`Template` フィールドには、1つ注意点があります。親テーマのフォルダー名と、`wp-content/themes` フォルダーからの相対距離が100％一致していなければなりません。このケースでは、Twenty Twenty-Four テーマフォルダーの場所は `wp-content/themes/twentytwentyfour` にあることが分かっています。したがって、`Template` の値は `twentytwentyfour` でなければなりません。

<!-- 
### Install and activate child theme
 -->

### 子テーマのインストールと有効化

<!-- 
If you are not already working within a development environment with your theme in the `wp-content/themes` folder, you’ll need to move it there now. Depending on your setup, you have several options, but the easiest is to create a ZIP file of your theme and upload it to your test site via **Appearance > Themes > Add New** in your WordPress admin.
 -->

まだ開発環境で `wp-content/themes` フォルダーにあなたのテーマを置いて作業していない場合は、今すぐそこに移動する必要があります。あなたのセットアップに応じて、いくつかのオプションがありますが、最も簡単なのは、あなたのテーマの ZIP ファイルを作成し、WordPress 管理画面の **外観 > テーマ > テーマを追加** 経由で、あなたのテストサイトにアップロードすることです。

<!-- 
For more information on how to add a theme to a WordPress, read [Adding New Themes](https://wordpress.org/documentation/article/work-with-themes/#adding-new-themes) from the WordPress Documentation site.
 -->

WordPress へのテーマ追加方法の詳細情報については、WordPress ドキュメント・サイトの [新規テーマの追加](https://wordpress.org/documentation/article/work-with-themes/#adding-new-themes) をご覧ください。

<!-- 
Once your theme is installed, visit **Appearance > Themes** in your WordPress admin and locate your theme. Click the **Activate** link as shown in this screenshot:
 -->

あなたのテーマをインストールしたら、あなたの WordPress 管理画面の **外観 > テーマ** にアクセスし、あなたのテーマを探します。このスクリーンショットに示すように、**有効化** リンクをクリックします:

<!-- 
[![WordPress Appearance > Themes screen showing the popup overlay of an empty child theme.](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?resize=2048%2C1055&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?ssl=1)
 -->

[![空の子テーマのポップアップ・オーバーレイを表示する、WordPress 外観 > テーマ画面。](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?resize=2048%2C1055&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?ssl=1)

<!-- 
It won’t look any different from your parent theme right now because you haven’t customized it yet. But you have successfully created a child theme.
 -->

まだカスタマイズしていないので、あなたの親テーマと、見た目は変わりません。しかし、これで子テーマの作成は成功です。

<!-- 
## Customizing your child theme
 -->

## あなたの子テーマのカスタマイズ

<!-- 
When customizing your child theme, all the functionality documented throughout this handbook is fully available to you. But there are a few considerations you should keep in mind, which you’ll learn about in the following sections.
 -->

あなたの子テーマをカスタマイズする際には、このハンドブックで説明されている機能は、すべて利用可能です。しかし、留意すべき点がいくつかあるので、以下のセクションで説明しましょう。

<!-- 
### Loading style.css
 -->

### style.css のロード

<!-- 
This is an optional step and often not needed for block themes because their style handling is generally done via [`theme.json`](https://developer.wordpress.org/themes/global-settings-and-styles/). But it is often necessary if you are building a classic theme. Regardless, you only need to perform this step if you want to ensure that any CSS code in `style.css` is loaded.
 -->

スタイルの処理は一般的に [`theme.json`](https://developer.wordpress.org/themes/global-settings-and-styles/) 経由で行われるため、これはオプションのステップで、ブロック・テーマでは必要ないことが多いです。しかし、クラシック・テーマを構築する場合には、しばしば必要なことです。いずれにせよ、`style.css` の CSS コードを確実にロードしたい場合のみ、このステップを実行する必要があります。

<!-- 
Before proceeding with this section, be sure to review the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation, which covers how to load `style.css` in more detail. In that documentation, you will learn how to enqueue stylesheets via the [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) function on the appropriate hook (note that child themes are loaded before their parent themes).
 -->

このセクションに進む前に、`style.css` をロードする方法について、より詳しく説明している、[アセットを含める](https://developer.wordpress.org/themes/core-concepts/including-assets/) ドキュメントを必ず確認してください。そのドキュメントでは、適切なフックの [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) 関数経由でスタイルシートをエンキューする方法を学びます (子テーマは、親テーマよりも先にロードされることに注意)。

<!-- 
The ideal method of enqueueing stylesheets is when a parent theme loads both its own `style.css` and the child theme’s `style.css`. But not all themes do this. Therefore, you must examine the code of the parent theme to see which stylesheets it is enqueueing. This is different for every theme, and there are no hard rules.
 -->

スタイルシートをエンキューする理想的な方法は、親テーマが自身の `style.css` と子テーマの `style.css` の両方をロードする場合です。しかし、すべてのテーマがそうしているわけではありません。したがって、親テーマのコードを調べて、どのスタイルシートがキューに入っているかを確認する必要があります。これはテーマごとに異なるもので、確固たるルールは存在しません。

<!-- 
If the parent theme loads both stylesheets, the child theme does not need to do anything. Its stylesheet will be automatically loaded.
 -->

親テーマが両方のスタイルシートをロードする場合、子テーマは何もする必要はありません。子テーマのスタイルシートは、自動的にロードされます。

<!-- 
In the case of the Twenty Twenty-Four theme, it doesn’t load a stylesheet at all. So you would have to load your `style.css` via `functions.php` as shown in this code snippet:
 -->

Twenty Twenty-Four テーマの場合、スタイルシートはまったくロードされません。したがって、このコード・スニペットに示されているように、`functions.php` 経由で、あなたの `style.css` をロードしなければなりません:

```php
add_action( 'wp_enqueue_scripts', 'grand_sunrise_enqueue_styles' );

function grand_sunrise_enqueue_styles() {
	wp_enqueue_style( 
		'grand-sunrise-style', 
		get_stylesheet_uri()
	);
}
```

<!-- 
If the parent theme you are using only loads its own stylesheet, you would also use the above code to load your child theme’s `style.css`.
 -->

使用している親テーマが独自のスタイルシートしかロードしない場合、上記のコードを使って、あなたの子テーマの `style.css` もロードすることになります。

<!-- 
If the parent theme loads only the active theme’s stylesheet, such as via `get_stylesheet_uri()`, then it will load the child theme’s stylesheet. In this case, you may want to also enqueue the parent theme’s stylesheet via `functions.php`, and your code would look like this:
 -->

親テーマが、たとえば `get_stylesheet_uri()` 経由で、有効化されているテーマのスタイルシートのみをロードする場合、子テーマのスタイルシートがロードされます。このケースでは、`functions.php` 経由で、親テーマのスタイルシートもエンキューしたいかもしれません。その場合、あなたのコードは次のようになるでしょう:

```php
add_action( 'wp_enqueue_scripts', 'grand_sunrise_enqueue_styles' );

function grand_sunrise_enqueue_styles() {
	wp_enqueue_style( 
		'grand-sunrise-parent-style', 
		get_parent_theme_file_uri( 'style.css' )
	);
}
```

<!-- 
### Templates, parts, and patterns
 -->

### テンプレート、パーツ、パターン

<!-- 
When building a child theme, you have the option to overwrite any template, part, or pattern that exists in the parent theme by adding a file of the same name in your child theme. *Note: patterns must also have the same registered `Slug` field.*
 -->

子テーマを構築する際、あなたの子テーマに同名ファイルを追加することで、親テーマに存在するテンプレート、パーツ、パターンを上書きするオプションがあります。*注: パターンも同じ登録 `Slug` フィールドがなければなりません。*

<!-- 
You can also add brand new templates, parts, and patterns to your child theme, even if they don’t exist in the parent. To learn more about these features, refer to these articles in the handbook:
 -->

親テーマに存在しなくても、あなたの子テーマにまったく新しいテンプレート、パーツ、パターンも追加できます。これらの機能の詳細については、ハンドブックのこれらの記事を参照してください:

<!-- 
*   [Templates](https://developer.wordpress.org/themes/templates/)
*   [Patterns](https://developer.wordpress.org/themes/features/block-patterns/)
 -->

*   [テンプレート](https://developer.wordpress.org/themes/templates/)
*   [パターン](https://developer.wordpress.org/themes/features/block-patterns/)

<!-- 
### Using functions.php
 -->

### functions.php の使用

<!-- 
Unlike templates and patterns, the `functions.php` file of a child theme does not override the `functions.php` file in the parent theme. In fact, they are both loaded, with the child being loaded immediately before the parent.
 -->

テンプレートやパターンとは異なり、子テーマの `functions.php` ファイルは、親テーマの `functions.php` ファイルをオーバーライドしません。実際、両者はロードされます (子は親のすぐ前にロードされる)。

<!-- 
In that way, the `functions.php` of a child theme provides a smart, trouble-free method of modifying the functionality of a parent theme or WordPress. 
 -->

このように、子テーマの `functions.php` は、親テーマや WordPress の機能をスマートに、トラブルなく変更する方法を提供します。

<!-- 
Suppose that you wanted to add a PHP function to your theme. The fastest way would be to open its `functions.php` file and put the function there. But that’s not considered a good practice—**the next time your theme is updated, your function will disappear!**
 -->

あなたのテーマに PHP 関数を追加したいとします。一番手っ取り早い方法は、`functions.php` ファイルを開いてそこに関数を置くことでしょう。しかし、それは良い習慣とは考えられていません — **次にあなたのテーマが更新されると、あなたの機能は消えてしまいます !**

<!-- 
It’s much better to create a child theme and add your custom code to your child theme’s `functions.php` file. The function will do the exact same job from there too, with the advantage that it will not be affected by future updates of the parent theme.
 -->

子テーマを制作し、あなたのカスタムコードをあなたの子テーマの `functions.php` ファイルに追加するほうが、ずっと良いでしょう。将来、親テーマがアップデートされても、この機能はそのテーマでもまったく同じ仕事をするようになり、影響を受けないという利点もあります。

<!-- 
Do not copy code directly from the `functions.php` of a parent theme into your child theme. That will likely lead to fatal errors because of duplicate function names.
 -->

親テーマの `functions.php` からあなたの子テーマに、直接コードをコピーしないでください。関数名が重複しているため、致命的なエラーにつながる可能性が高いのです。

<!-- 
To learn more about `functions.php`, check out the [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) documentation.
 -->

`functions.php` についての詳細を知りたい人は、[カスタム機能](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) ドキュメントをご覧ください。

<!-- 
### Referencing or including other files
 -->

### 他のファイルの参照またはインクルード

<!-- 
Sometimes you need to include or use custom files in your theme. When doing so, you need to make sure that you’re using the function that will give you the correct directory path or URI based on your child theme’s directory.
 -->

あなたのテーマに、カスタムファイルをインクルードまたは使用する必要がある場合があります。そうする際には、あなたの子テーマのディレクトリにもとづいて、正しいディレクトリ・パスまたは URI を与える関数の使用を確認する必要があります。

<!-- 
For example, if you wanted to include another PHP file via your `functions.php`, you would use the [`get_theme_file_path()`](https://developer.wordpress.org/reference/functions/get_theme_file_path/) function. Here is a code snippet that shows including a `functions-helpers.php` file from an `/inc` folder in your child theme:
 -->

たとえば、あなたの `functions.php` 経由で別の PHP ファイルをインクルードしたい場合は、[`get_theme_file_path()`](https://developer.wordpress.org/reference/functions/get_theme_file_path/) 関数を使用します。以下は、あなたの子テーマに `/inc` フォルダーの `functions-helpers.php` ファイルを含めることを示す、コードスニペットです:

```php
require_once get_theme_file_path( 'inc/functions-helpers.php' );
```

<!-- 
To learn more about including files, read the [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) documentation.
 -->

ファイルのインクルードに関する詳細ついては、[カスタム機能](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) ドキュメントをご覧ください。

<!-- 
When you need to reference a file by its URL, such as an image or stylesheet, you must use a different function: [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/). Let’s look at an example of using a file named `bunny.jpg` from your theme’s `/assets/images` folder in an `<img>` HTML tag:
 -->

画像やスタイルシートなど、URL でファイルを参照する必要がある場合は、別の関数を使う必要があります: [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/)。あなたのテーマの `/assets/images` フォルダーにある `bunny.jpg` という名称のファイルを、HTML タグ `<img>` の中で使う例を見てみましょう:

```php
<?php $image = get_theme_file_uri( 'assets/images/bunny.jpg' ); ?>

<img src="<?php echo esc_url( $image ); ?>" alt="" />
```

<!-- 
You can find out more about including scripts, styles, images, and other assets from the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation.
 -->

スクリプト、スタイル、画像、その他のアセットのインクルードに関する詳細については、[アセットを含める](https://developer.wordpress.org/themes/core-concepts/including-assets/) ドキュメントをご覧ください。

<!-- 
### Internationalization
 -->

### 国際化

<!-- 
Like parent themes, child themes can also be internationalized and made to work in any language. To learn more, read the [Internationalization](https://developer.wordpress.org/themes/advanced-topics/internationalization/) documentation in the Theme Handbook.
 -->

親テーマと同様に、子テーマも国際化し、どの言語でも動作するようにできます。詳細については、テーマ・ハンドブックの [国際化](https://developer.wordpress.org/themes/advanced-topics/internationalization/) ドキュメントをご覧ください。

<!-- 
The biggest changes, as noted in the Internationalization documentation, are that you must create a unique text domain and use [`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) instead of [`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/) when manually loading translations.
 -->

国際化のドキュメントで述べられているように、手動で翻訳をロードする場合、最大の変更点は、一意のテキスト・ドメインを作成し、[`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/) の代わりに、[`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) を使用する必要があることです。