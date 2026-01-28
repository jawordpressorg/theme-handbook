<!-- 
# 404 Pages
 -->

# 404エラー・ページ

<!-- 
A 404 page is important to add into your theme in case a user stumbles upon a page that doesn’t exist or hasn’t been created yet. It is also important that your 404 page gives your visitors a way to arrive at the right place.
 -->

ユーザーが、存在しないページや未作成のページにアクセスした場合に備え、あなたのテーマに404エラー・ページを追加することは重要です。また、あなたの404エラー・ページが、あなたの訪問者に対して、正しい場所へ到達する手段を提供することも重要です。

<!-- 
These next few steps will help you build a useful 404 page for your WordPress theme.
 -->

次の数ステップで、あなたの WordPress テーマに、役立つ404エラー・ページを構築できます。

<!-- 
## Creating the 404.php file
 -->

## `404.php` ファイルの作成

<!-- 
As the `404.php` file is used on a page not found error, the first step is to create a file named `404.php` and add it to your WordPress theme folder.
 -->

`404.php` ファイルは、ページが見つからないエラーの際に使用されるため、最初のステップとして、あなたの WordPress テーマフォルダー内に、`404.php` という名称のファイルを作成し、追加します。

<!-- 
Often times a great starting point for your `404.php` is your `index.php`
 -->

多くの場合、あなたの `404.php` の優れた出発点は、あなたの `index.php` です。

<!-- 
## Add a file header
 -->

## ファイル・ヘッダーの追加

<!-- 
To use your theme’s `header.php` file, open your `404.php` file. At the top, add a comment describing what the file is and make sure you include your theme’s header.
 -->

あなたのテーマの `header.php` ファイルを使用するために、あなたの `404.php` ファイルを開きます。ファイルの先頭に、このファイルが何であるかを説明するコメントを追加し、必ずあなたのテーマのヘッダーをインクルードするようにしてください。

<!-- 
For example:
 -->

たとえば:

```php
/**
 * The template for displaying 404 pages (Not Found)
 */
get_header();
```

<!-- 
## Adding the body to your 404 Page
 -->

## あなたの404エラー・ページに、`body` の追加

<!-- 
To make the 404 page functional you have to add the body content to your template:
 -->

404エラー・ページを機能させるには、あなたのテンプレートに body コンテンツを追加する必要があります:

<!-- 
Example:
 -->

例:

```php
<div id="primary" class="content-area">
		<div id="content" class="site-content" role="main">

			<header class="page-header">
				<h1 class="page-title"><?php _e( 'Not Found', 'twentythirteen' ); ?></h1>
			</header>

			<div class="page-wrapper">
				<div class="page-content">
					<h2><?php _e( 'This is somewhat embarrassing, isn’t it?', 'twentythirteen' ); ?></h2>
					<p><?php _e( 'It looks like nothing was found at this location. Maybe try a search?', 'twentythirteen' ); ?></p>

					<?php get_search_form(); ?>
				</div><!-- .page-content -->
			</div><!-- .page-wrapper -->

		</div><!-- #content -->
	</div><!-- #primary -->
```

<!-- 
This example is from the Twenty Thirteen theme that comes with WordPress. This adds some text and a search form in the 404 page.
 -->

本例は、WordPress に付属する「Twenty Thirteen」テーマに由来します。これにより、404エラー・ページにテキストと検索フォームが追加されます。

<!-- 
You can to add your own text to make your 404 page look better.
 -->

独自のテキストを追加して、あなたの404エラー・ページを、より見栄え良くできます。

<!-- 
## Adding the footer and sidebar.
 -->

## フッターとサイドバーの追加

<!-- 
The final step when creating a 404 page is to add the footer. You may also add a sidebar if you want.
 -->

404エラー・ページを作成する最終ステップは、フッターを追加することです。必要に応じて、サイドバーも追加できます。

<!-- 
Example:
 -->

例:

```php
get_sidebar();
get_footer();
```

<!-- 
Now you have a functional 404 page with a search form and some text in case a user stumbles upon the wrong page. Once you make sure the `404.php` has been uploaded, you can test your 404 page. Just type a URL address for your website that doesn’t exist. You can try something like `http://example.com/fred.php`. This is sure to result in a 404 error unless you actually have a PHP file called `` fred.php`.` ``
 -->

これで、検索フォームと、ユーザーが間違ったページにアクセスした場合のテキストを備えた、機能的な404エラー・ページが完成しました。`404.php` がアップロードされたことを確認したら、あなたの404エラー・ページをテストできます。存在しないあなたの Web サイト URL を入力してみましょう。たとえば `http://example.com/fred.php` のような URL を試してみましょう。実際に `fred.php` という PHP ファイルが存在しない限り、必ず404エラーが表示されます。