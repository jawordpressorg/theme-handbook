<!-- 
# Partial and Miscellaneous Template Files
 -->

# パーシャル・テンプレート・ファイルと、その他のテンプレート・ファイル

<!-- 
## Introduction
 -->

## はじめに

<!-- 
Not all template files generate the entire content that will be rendered by the browser. Some template files are pulled in by other template files such as `comments.php`, `header.php`, `footer.php`, `sidebar.php` and `content-{$slug}.php`. You’ll walk through each of these template files to get an understanding of the purpose and how to build them.
 -->

すべてのテンプレート・ファイルが、ブラウザーによってレンダリングされるコンテンツ全体を生成するわけではありません。一部のテンプレートファイル (`comments.php`、`header.php`、`footer.php`、`sidebar.php`、`content-{$slug}.php` など) は、他のテンプレート・ファイルによって挿入されます。これらの各テンプレート・ファイルについて、その目的と構築方法を理解するために、順を追って説明します。

<!-- 
## Header.php
 -->

## `header.php`

<!-- 
The `header.php` file does exactly what you would expect.  It contains all the code that the browser will render for the header. This is a partial template file because unless a different template file calls the [template tag](https://developer.wordpress.org/themes/basics/template-tags/), `get_header()`, the browser will not render the contents of this file.
 -->

`header.php` ファイルは、まさに期待通りのものになります。このファイルには、ブラウザーがヘッダーとしてレンダリングする、すべてのコードが含まれています。このファイルはパーシャル・テンプレート・ファイルです。別のテンプレート・ファイルが [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) `get_header()` をコールしない限り、ブラウザーは本ファイルのコンテンツをレンダリングしません。

<!-- 
Often sites have the same header regardless of the page or post you’re on.  However, some sites have slight variations such as a secondary navigation or different banner image depending on the page. Your `header.php` file can handle all these variations if you use [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/).
 -->

多くのサイトでは、閲覧しているページや投稿に関係なく、常に同じヘッダーが表示されます。しかしながら、一部のサイトでは、ページに応じて第2ナビゲーションや異なるバナー画像など、わずかなバリエーションが設けられています。[条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/) を使用すれば、あなたの `header.php` ファイルで、これらすべてのバリエーションを処理できます。

<!-- 
Almost all themes have a `header.php` file as the functionality and maintainability of this file pretty much demands its creation.
 -->

機能性と保守性の観点から、その作成がほぼ必須であるため、ほぼすべてのテーマには、`header.php` ファイルが存在します。

<!-- 
Below is an example of a header.php found in the twenty fifteen theme.
 -->

以下は、「Twenty Fifteen」テーマに含まれる、`header.php` の例です。

```php
<!DOCTYPE html>
<html <?php language_attributes(); ?> class="no-js">
<head>
    <meta charset="<?php bloginfo( 'charset' ); ?>">
    <meta name="viewport" content="width=device-width">
    <link rel="profile" href="http://gmpg.org/xfn/11">
    <link rel="pingback" href="<?php bloginfo( 'pingback_url' ); ?>">
    <!--[if lt IE 9]>
    <script src="<?php echo esc_url( get_template_directory_uri() ); ?>/js/html5.js"></script>
    <![endif]-->
    <?php wp_head(); ?>
</head>
 
<body <?php body_class(); ?>>
    <div id="page" class="hfeed site">
        <a class="skip-link screen-reader-text" href="#content"><?php _e( 'Skip to content', 'twentyfifteen' ); ?></a>
        <div id="sidebar" class="sidebar">
            <header id="masthead" class="site-header" role="banner">
                <div class="site-branding">
                    <?php if ( is_front_page() && is_home() ) : ?>
                    <h1 class="site-title">
                        <a href="<?php echo esc_url( home_url( '/' ) ); ?>" rel="home"><?php bloginfo( 'name' ); ?></a>
                    </h1>
                    <?php else : ?>
                    <a href="<?php echo esc_url( home_url( '/' ) ); ?>" rel="home"><?php bloginfo( 'name' ); ?></a>
                    <?php endif;
                    $description = get_bloginfo( 'description', 'display' );
                    if ( $description || is_customize_preview() ) :
                        echo $description;
                    endif; ?>
                    <button class="secondary-toggle"><?php _e( 'Menu and widgets', 'twentyfifteen' ); ?></button>
                </div><!-- .site-branding -->
            </header><!-- .site-header -->
            <?php get_sidebar(); ?>
        </div><!-- .sidebar -->
        <div id="content" class="site-content">
```

<!-- 
Some of the code may look a little daunting at first, but if we break it down, it becomes simple enough. After the opening commment, the `head` is created. The template tag `wp_head()` pulls in all of our styles and any scripts that would appear in the head rather than the footer that we enqueued in our `functions.php` file.
 -->

一部のコードは最初に見ると少し難しそうに思えるかもしれませんが、分解すれば十分にシンプルになります。冒頭コメントの後、`head` が作成されます。テンプレート・タグ `wp_head()` は、私達の `functions.php` ファイルでキューに登録したスタイルやスクリプトを、フッターではなくヘッダーに挿入します。

<!-- 
Next, the `body` is opened and a mix of HTML and PHP are present. You can see some conditional tags in the site branding div that tweak a little bit of what is shown based on the page the user is on. Then the site navigation is pulled in. Lastly, the main site-content div is opened which will be closed most likely in the `footer.php` file.
 -->

続けて、`body` が開かれ、HTML と PHP が混在しています。サイト・ブランディング `div` 内には、条件付きタグがいくつかあり、ユーザーが閲覧しているページにもとづいて、表示内容を微調整しています。その後、サイト・ナビゲーションが挿入されます。最後に、メインのサイト・コンテンツ `div` が開かれ、これはおそらく `footer.php` ファイル内で閉じられます。

<!-- 
One important template tag to note is `body_class()` found in the opening `body` tag. This is a super handy tag that makes styling your theme a lot easier by giving your body classes depending on the template file and other settings being used.
 -->

特筆すべき重要なテンプレート・タグの一つが、`body` 開始タグ内で使用される `body_class()` です。これは非常に便利なタグで、使用中のテンプレート・ファイルやその他の設定に応じて、あなたの `body` クラスを付与することで、あなたのテーマのスタイリングを大幅に容易にします。

<!-- 
## Footer.php
 -->

## `footer.php`

<!-- 
Much like the `header.php` file the `footer.php` is a very common template file that most themes utilize. The code in the `footer.php` file will not be rendered unless another template file pulls in the `footer.php` with `get_footer()` [template tag](https://developer.wordpress.org/themes/basics/template-tags/).  Similarly to headers, you can make variations of footers using [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/).
 -->

`header.php` ファイルと同様に、`footer.php` もほとんどのテーマで利用される、非常に一般的なテンプレート・ファイルです。`footer.php` ファイル内のコードは、別のテンプレート・ファイルが `get_footer()` [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) で `footer.php` を挿入しない限り、レンダリングされません。ヘッダーと同様に、フッターも [条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/) を使用してバリエーションを作成できます。

<!-- 
Often developers will put [widgetized areas](https://developer.wordpress.org/themes/functionality/widgets/) in the footer so that the end user can easily drop and drag different content types into the footer.
 -->

開発者はしばしばフッターに [ウィジェット化領域](https://developer.wordpress.org/themes/functionality/widgets/) を設置し、エンドユーザーが異なるコンテンツ・タイプをドラッグ & ドロップで簡単に、フッターに配置できるようにします。

<!-- 
Here is an example of a `footer.php` file from the Twenty Fifteen theme.
 -->

以下は、「Twenty Fifteen」テーマにおける、`footer.php` ファイルの例です。

```php
</div><!-- .site-content -->

<footer id="colophon" class="site-footer" role="contentinfo">

	<div class="site-info">

		<?php
		/**
		 * Fires before the Twenty Fifteen footer text for footer customization.
		 *
		 * @since Twenty Fifteen 1.0
		 */
		do_action( 'twentyfifteen_credits' );
		?>
		<a href="<?php echo esc_url( __( 'https://wordpress.org/', 'twentyfifteen' ) ); ?>"><?php printf( __( 'Proudly powered by %s', 'twentyfifteen' ), 'WordPress' ); ?></a>

	</div><!-- .site-info -->

</footer><!-- .site-footer -->

</div><!-- .site -->

<?php wp_footer(); ?>

</body>
</html>
```

<!-- 
## 404.php
 -->

## `404.php`

<!-- 
When users try to visit a page on your website that doesn’t exist they’ll be directed to your `index.php` page unless you’ve created a 404.php template.  It’s a good idea to have some sort of message that the explains the page is missing or no longer available.  Creating this template helps keep the visual aspects of your theme consistent and provides your end users with helpful information.
 -->

ユーザーがあなたの Web サイト上に存在しないページに対してアクセスしようとすると、`404.php` テンプレートを作成していない限り、あなたの `index.php` ページにリダイレクトされます。ページが存在しない、または利用できなくなったことを説明する、何らかのメッセージを用意しておくことが望ましいです。このテンプレートを作成することで、あなたのテーマの視覚的な側面の一貫性を保ち、あなたのエンドユーザーに有益な情報を提供します。

<!-- 
Here is an example of a 404.php template file from the twenty fifteen theme.
 -->

以下は、「Twenty Fifteen」テーマにおける `404.php` テンプレート・ファイルの例です。

```php
<?php get_header(); ?>

<div id="primary" class="content-area">

	<main id="main" class="site-main" role="main">

		<section class="error-404 not-found">

			<header class="page-header">
				<h1 class="page-title"><?php _e( 'Oops! That page can’t be found.', 'twentyfifteen' ); ?></h1>
			</header><!-- .page-header -->

			<div class="page-content">
				<?php _e( 'It looks like nothing was found at this location. Maybe try a search?', 'twentyfifteen' ); ?>
				<?php get_search_form(); ?>
			</div><!-- .page-content -->

		</section><!-- .error-404 -->

	</main><!-- .site-main -->

</div><!-- .content-area -->

<?php get_footer(); ?>
```

<!-- 
## Comments.php
 -->

## `comments.php`

<!-- 
The `comments.php` file handles exactly what you would expect, comments. This is a partial template that is pulled into other template files to display comments that users leave on a page or post. Several different pages and posts show comments so it makes sense to have one file that can be pulled in when needed.
 -->

`comments.php` ファイルは、その名の通り、コメントを扱うファイルです。これは、ユーザーがページや投稿に残したコメントを表示するために、他のテンプレート・ファイルに挿入される、パーシャル・テンプレートです。複数の異なるページや投稿でコメントを表示するため、必要に応じて挿入できる、単一ファイルを用意するのが合理的です。

<!-- 
The code involved in creating comments is expanded upon on the [comment template page](https://developer.wordpress.org/themes/template-files-section/partial-and-miscellaneous-template-files/comments/).
 -->

コメント作成に関連するコードの詳細は、[コメント・テンプレート・ページ](https://developer.wordpress.org/themes/template-files-section/partial-and-miscellaneous-template-files/comments/) で説明されています。

<!-- 
## Sidebar.php
 -->

## `sidebar.php`

<!-- 
A lot of themes utilize sidebars to display widgets.  For a sidebar to work in a theme it must be registered and then a template file for the sidebar must be created.  You’ll learn more about [registering sidebars](https://developer.wordpress.org/themes/functionality/sidebars/) in a later chapter. Sidebar files often have conditional statements and the `is_active_sidebar( 'sidebar-name' )` function in them to ensure a widget is in use within the sidebar so that empty HTML isn’t added to a page unnecessarily.
 -->

多くのテーマでは、ウィジェットを表示するために、サイドバーを利用しています。テーマでサイドバーを機能させるには、サイドバーを登録し、サイドバー用のテンプレート・ファイルを作成する必要があります。[サイドバーの登録](https://developer.wordpress.org/themes/functionality/sidebars/)については、後の章でさらに詳しく学びます。サイドバー・ファイルには、ウィジェットがサイドバー内で使用されていることを確認するための条件文や `is_active_sidebar( 'sidebar-name' )` 関数が含まれていることが多く、これにより不要な空の HTML がページに追加されるのを防ぎます。

<!-- 
Here is an example of a sidebar template file from the twenty fifteen theme. Notice at the bottom the sidebar is pulled in using `<?php dynamic_sidebar( 'sidebar-1' ); >`. Now whatever, widgets are put into that sidebar will display on the page that is using this pulling in this template.
 -->

以下は、「Twenty Fifteen」テーマにおける、サイドバー・テンプレート・ファイルの例です。下部で、`<?php dynamic_sidebar( 『sidebar-1』 ); >` によって、サイドバーが挿入されていることに注目してください。さて、とにかく、そのサイドバーに配置されたウィジェットは、このテンプレートを挿入したページに表示されます。

```php
<?php if ( has_nav_menu( 'primary' ) || has_nav_menu( 'social' ) || is_active_sidebar( 'sidebar-1' ) ) : ?>

	<div id="secondary" class="secondary">

		<?php if ( is_active_sidebar( 'sidebar-1' ) ) : ?>
			<div id="widget-area" class="widget-area" role="complementary">
				<?php dynamic_sidebar( 'sidebar-1' ); ?>
			</div><!-- .widget-area -->
		<?php endif; ?>

	</div><!-- .secondary -->

<?php endif; ?>
```

<!-- 
## Content-{$slug}.php
 -->

## `content-{$slug}.php`

<!-- 
Many theme developers break their template files into small bite sized pieces.  They’ll often put wrappers and page architecture elements in template files like `page.php, home.php, comments.php` etc but then they put the code displaying the content of those pages in another template file. Enter `content-{$slug}.php`: common examples would be `content-page.php, content-post.php, content-portfolio.php, content-none.php`.  These are not file names that WordPress recognizes and will interpret a certain way, rather they are a common approach to display specific types of content.
 -->

多くのテーマ開発者は、テンプレート・ファイルを小さな単位に分割します。彼らはよく、ラッパーやページ構造要素を `page.php`、`home.php`、`comments.php` などのテンプレート・ファイルに配置しますが、それらのページのコンテンツを実際に表示するコードは、別のテンプレート・ファイルに配置します。`content-{$slug}.php` を入力してください: 一般的な例としては、`content-page.php`、`content-post.php`、`content-portfolio.php`、`content-none.php` などがあります。これらは WordPress が認識し特定の方法で解釈するファイル名ではなく、特定の種類のコンテンツを表示するための一般的なアプローチです。

<!-- 
For example, often on blog posts you want to display the author’s name, the date of the post, and possibly the category of the post.  You’d also likely have links to previous and next posts. That information wouldn’t be appropriate on a regular page. Similarly on a portfolio page you would likely have a featured image or gallery you would want to display in a way differently than say a blog post’s or page’s featured images.
 -->

たとえば、ブログ投稿では、作者名、投稿日、場合によっては投稿のカテゴリーを掲載したい場合がよくあります。また、前の投稿と次の投稿へのリンクも、用意することでしょう。その情報は、通常のページには適していません。同様に、ポートフォリオ・ページでは、ブログ投稿やページのアイキャッチ画像とは異なる方法で表示したい、アイキャッチ画像やギャラリーを用意することでしょう。

<!-- 
You’ll want to use the `get_template_part()` [template tag](https://developer.wordpress.org/themes/basics/template-tags/) to pull in the `content-{$slug}.php` file. To pull in your `content-page.php` file you would call `get_template_part( 'content', 'page' );`
 -->

`content-{$slug}.php` ファイルを挿入する際には、`get_template_part()` [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) を使用したいところでしょう。あなたの `content-page.php` ファイルを挿入するには、`get_template_part( 'content', 'page' )` をコールします;

<!-- 
Here is twenty fifteen’s example of a `content-page.php` template file.
 -->

以下は、「Twenty Fifteen」における、`content-page.php` テンプレート・ファイルの例です。

```php
<article id="post-<?php the_ID(); ?>" <?php post_class(); ?>>

	<header class="entry-header">
		<?php the_title( '<h1 class="entry-title">', '</h1>' ); ?>
	</header><!-- .entry-header -->

	<div class="entry-content">
		<?php the_content(); ?>
		<?php
		wp_link_pages( array(
			'before'      => '<div class="page-links"><span class="page-links-title">' . __( 'Pages:', 'twentyfifteen' ) . '</span>',
			'after'       => '</div>',
			'link_before' => '<span>',
			'link_after'  => '</span>',
			'pagelink'    => '<span class="screen-reader-text">' . __( 'Page', 'twentyfifteen' ) . ' </span>%',
			'separator'   => '<span class="screen-reader-text">, </span>',
		) );
		?>
	</div><!-- .entry-content -->

	<?php edit_post_link( __( 'Edit', 'twentyfifteen' ), '<footer class="entry-footer"><span class="edit-link">', '</span></footer><!-- .entry-footer -->' ); ?>

</article><!-- #post-## -->
```