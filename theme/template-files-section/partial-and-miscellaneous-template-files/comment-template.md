<!-- 
# Comment Template
 -->

# コメント・テンプレート

<!-- 
WordPress displays comments in your theme based on the settings and code in the `comments.php` file within your WordPress theme.
 -->

WordPress は、あなたの WordPress テーマ内の `comments.php` ファイル内の設定とコードにもとづいて、あなたのテーマにコメントを表示します。

<!-- 
## Simple comments loop
 -->

## シンプルなコメント・ループ

```php
// Get only the approved comments
$args = array(
	'status' => 'approve',
);

// The comment Query
$comments_query = new WP_Comment_Query();
$comments       = $comments_query->query( $args );

// Comment Loop
if ( $comments ) {
	foreach ( $comments as $comment ) {
		echo '<p>' . $comment->comment_content . '</p>';
	}
} else {
	echo 'No comments found.';
}
```

<!-- 
The `comments.php` template contains all the logic needed to pull comments out of the database and display them in your theme.
 -->

`comments.php` テンプレートには、データベースからコメントを取得し、あなたのテーマに表示するために必要な、すべてのロジックが含まれています。

<!-- 
Before we explore the template file you’ll want to know how to pull in the partial template file on the appropriate pages such as `single.php`. You’ll wrap the comment [template tag](https://developer.wordpress.org/themes/basics/template-tags/) in a conditional statement so comments.php is only pulled in if it makes sense to do.
 -->

テンプレート・ファイルを詳しく見る前に、`single.php` などの適切なページで、パーシャル・テンプレート・ファイルを挿入する方法を知っておく必要があります。コメント [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) を条件文で囲むことで、`comments.php` は、必要な場合にのみ、挿入されます。

```php
// If comments are open or we have at least one comment, load up the comment template.
if ( comments_open() || get_comments_number() ) :
	comments_template();
endif;
```

<!-- 
![functionality-comments-01](https://i0.wp.com/developer.wordpress.org/files/2014/10/functionality-comments-01.png?resize=350%2C257&ssl=1)
 -->

![functionality-comments-01](https://i0.wp.com/developer.wordpress.org/files/2014/10/functionality-comments-01.png?resize=350%2C257&ssl=1)

<!-- 
## Another comments.php Example
 -->

## `comments.php` の別の例

<!-- 
Here’s an example of the `comments.php` template included with the Twenty Thirteen theme:
 -->

「Twenty Thirteen」テーマに含まれる `comments.php` テンプレートの例を、以下に示します:

```php
<?php
/**
 * The template for displaying Comments.
 *
 * The area of the page that contains comments and the comment form.
 *
 * @package WordPress
 * @subpackage Twenty_Thirteen
 * @since Twenty Thirteen 1.0
 */

/*
 * If the current post is protected by a password and the visitor has not yet
 * entered the password we will return early without loading the comments.
 */
if ( post_password_required() ) {
	return;
}
?>

<div id="comments" class="comments-area">

	<?php if ( have_comments() ) : ?>
		<h2 class="comments-title">
			<?php
			printf(
				_nx(
					'One thought on "%2$s"',
					'%1$s thoughts on "%2$s"',
					get_comments_number(),
					'comments title',
					'twentythirteen'
				),
				number_format_i18n( get_comments_number() ),
				'<span>' . get_the_title() . '</span>'
			);
			?>
		</h2>

		<ol class="comment-list">
			<?php
			wp_list_comments( array(
				'style'       => 'ol',
				'short_ping'  => true,
				'avatar_size' => 74,
			) );
			?>
		</ol><!-- .comment-list -->

		<?php if ( get_comment_pages_count() > 1 && get_option( 'page_comments' ) ) : ?>
			<nav class="navigation comment-navigation" role="navigation">

				<h1 class="screen-reader-text section-heading"><?php _e( 'Comment navigation', 'twentythirteen' ); ?></h1>
				<div class="nav-previous"><?php previous_comments_link( __( '&larr; Older Comments', 'twentythirteen' ) ); ?></div>
				<div class="nav-next"><?php next_comments_link( __( 'Newer Comments &rarr;', 'twentythirteen' ) ); ?></div>
			</nav><!-- .comment-navigation -->
		<?php endif; // Check for comment navigation ?>

		<?php if ( ! comments_open() && get_comments_number() ) : ?>
			<p class="no-comments"><?php _e( 'Comments are closed.', 'twentythirteen' ); ?></p>
		<?php endif; ?>

	<?php endif; // have_comments() ?>

	<?php comment_form(); ?>

</div><!-- #comments -->
```

<!-- 
## Breaking down the comments.php
 -->

## `comments.php` の分解

<!-- 
The above `comments.php` can be broken down to the below parts for better understanding.
 -->

上記の `comments.php` は、理解を深めるために、以下のパーツに分解できます。

<!-- 
1.  [Template Header](#template-header)
2.  [Comments Title](#comments-title)
3.  [Comment Listing](#comment-listing)
4.  [Comment Pagination](#comment-pagination)
5.  [Comments are closed message](#comments-are-closed-message).
6.  [The End](#the-end)
 -->

1.  [テンプレート・ヘッダー](#template-header)
2.  [コメント・タイトル](#comments-title)
3.  [コメント一覧](#comment-listing)
4.  [コメントのページ送り](#comment-pagination)
5.  [「コメントは、受け付けていません。」メッセージ](#comments-are-closed-message)
6.  [終わり](#the-end)

<!-- 
### Template Header
 -->

### テンプレート・ヘッダー

<!-- 
This template begins by identifying the template.
 -->

本テンプレートは、テンプレートの識別から始まります。

```php
<?php
/**
 * The template for displaying Comments.
 *
 * The area of the page that contains comments and the comment form.
 *
 * @package WordPress
 * @subpackage Twenty_Thirteen
 * @since Twenty Thirteen 1.0
 */
```

<!-- 
Next, there’s a test to see if the post is password protected and, if so, it stops processing the template.
 -->

続いて、投稿がパスワード保護されているかどうかを確認するテストが行われ、保護されている場合は、テンプレートの処理を停止します。

```php
/*
 * If the current post is protected by a password and the visitor has not yet
 * entered the password we will return early without loading the comments.
 */
if ( post_password_required() )
 return;
?>
```

<!-- 
Finally, there’s a test to see if there are comments associated with this post.
 -->

最後に、この投稿に関連付けられたコメントがあるかどうかを確認するテストがあります。

```php
<div id="comments" class="comments-area">
	<?php if ( have_comments() ) : ?>
```

<!-- 
### Comments Title
 -->

### コメント・タイトル

<!-- 
Prints out the header that appears above the comments.
 -->

コメントの上部に表示されるヘッダーを出力します。

<!-- 
Uses the [\_nx()](https://developer.wordpress.org/reference/functions/_nx/) translation function so other developers can provide alternative language translations.
 -->

[`_nx()`](https://developer.wordpress.org/reference/functions/_nx/) 翻訳関数を使用することで、他開発者が代替言語の翻訳を提供できます。

```php
<h2 class="comments-title">
	<?php
	printf(
		_nx(
			'One thought on "%2$s"',
			'%1$s thoughts on "%2$s"',
			get_comments_number(),
			'comments title',
			'twentythirteen'
		),
		number_format_i18n( get_comments_number() ),
		'<span>' . get_the_title() . '</span>'
	);
	?>
</h2>
```

<!-- 
### Comment Listing
 -->

### コメント一覧

<!-- 
The following snippet creates an ordered listing of comments using the [wp\_list\_comments()](https://developer.wordpress.org/reference/functions/wp_list_comments/) function.
 -->

以下のスニペットは、[`wp_list_comments()`](https://developer.wordpress.org/reference/functions/wp_list_comments/) 関数を使用して、コメントの番号付きリストを作成します。

```php
<ol class="comment-list">
	<?php
	wp_list_comments( array(
		'style'       => 'ol',
		'short_ping'  => true,
		'avatar_size' => 74,
	) );
	?>
</ol><!-- .comment-list -->
```

<!-- 
### Comment Pagination
 -->

### コメントのページ送り

<!-- 
Checks to see if there are enough comments to merit adding comment navigation and, if so, create comment navigation.
 -->

コメント・ナビゲーションを追加する価値があるほど十分なコメントがあるか否かをチェックし、該当する場合はコメント・ナビゲーションを作成します。

```php
<?php if ( get_comment_pages_count() > 1 && get_option( 'page_comments' ) ) : ?>

	<nav class="navigation comment-navigation" role="navigation">

		<h3 class="screen-reader-text section-heading"><?php _e( 'Comment navigation', 'twentythirteen' ); ?></h3>
		<div class="nav-previous"><?php previous_comments_link( __( '&larr; Older Comments', 'twentythirteen' ) ); ?></div>
		<div class="nav-next"><?php next_comments_link( __( 'Newer Comments &rarr;', 'twentythirteen' ) ); ?></div>

	</nav><!-- .comment-navigation -->

<?php endif; // Check for comment navigation ?>
```

<!-- 
### Comments are closed message.
 -->

### コメントは、受け付けていません。

<!-- 
If comments aren’t open, displays a line indicating that they’re closed.
 -->

コメントを受け付けていない場合、コメントを受け付けていないことを示す行を表示します。

```php
<?php if ( ! comments_open() && get_comments_number() ) : ?>
	<p class="no-comments"><?php _e( 'Comments are closed.', 'twentythirteen' ); ?></p>
<?php endif; ?>
```

<!-- 
### The End
 -->

### 終わり

<!-- 
This section ends the comments loop, includes the comment form, and closes the comment wrapper.
 -->

本セクションはコメント・ループを終了し、コメント・フォームをインクルードし、コメント・ラッパーを閉じます。

```php
	<?php endif; // have_comments() ?>

	<?php comment_form(); ?>

</div><!-- #comments -->
```

<!-- 
## Comments Pagination
 -->

## コメントのページ送り

<!-- 
If you have a lot of comments (which makes your page long), then there are a number of potential benefits to paginating your comments. Pagination helps improve page load speed, especially on mobile devices.  
Enabling comments pagination is done in two steps.
 -->

(それによりページが長くなる) コメントが大量にある場合、コメントをページ分割することには、いくつかの利点があります。ページ分割は、特にモバイル端末において、ページのロード速度向上に役立ちます。
コメントのページ分割を有効にするには、次の2つの手順で設定します。

<!-- 
1.  Enable paged comments within WordPress by going to *Settings* > *Discussion* , and checking the box “*Break comments into pages*” . You can enter any number for the “*top level comments per page*”.
2.  Open your `comments.php` template file and add the following line where you want the comment pagination to appear.
 -->

1.  WordPress でコメントのページ送りを有効にするには、*設定 > ディスカッション* に移動し、「*コメントを複数ページに分割する*」のチェックボックスをオンにします。「*ページごとのトップレベルのコメント*」には、任意の数値を入力できます。
2.  あなたの `comments.php` テンプレート・ファイルを開き、コメントのページ送りを表示したい場所に、次の行を追加します。

```php
<div class="pagination">
	<?php paginate_comments_links(); ?>
</div>
```

<!-- 
## Alternative Comment Template
 -->

## 代替コメント・テンプレート

<!-- 
On some occasions you may want display your comments differently within your theme. For this you would build an alternate file (ex. short-comments.php) and call it as follows:
 -->

場合によっては、あなたのテーマ内で、コメントを異なる形式で表示したいと思うかもしれません。その場合は、代替ファイル (例: `short-comments.php`) を作成し、以下のようにコールします:

```php
<?php comments_template( '/short-comments.php' );
```

<!-- 
The path to the file used for an alternative comments template should be relative to the current theme root directory, and include any subfolders. So if the custom comments template is in a folder inside the theme, it may look like this when called:
 -->

代替コメント・テンプレートに使用されるファイルへのパスは、現在のテーマ・ルート・ディレクトリからの相対パスとし、サブ・フォルダーもすべて含める必要があります。カスタム・コメント・テンプレートがテーマ内のフォルダーにある場合、コールされた際の見え方は、次のようになります:

```php
<?php comments_template( '/custom-templates/alternative-comments.php' );
```

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
*   [wp\_list\_comments()](https://developer.wordpress.org/reference/functions/wp_list_comments/) : Displays all comments for a post or Page based on a variety of parameters including ones set in the administration area.
*   [comment\_form()](https://developer.wordpress.org/reference/functions/comment_form/) : This tag outputs a complete commenting form for use within a template.
*   [comments\_template()](https://developer.wordpress.org/reference/functions/comments_template/) : Load the comment template specified in first argument
*   [paginate\_comments\_links()](https://developer.wordpress.org/reference/functions/paginate_comments_links/) : Create pagination links for the comments on the current post.
*   [get\_comments()](https://developer.wordpress.org/reference/functions/get_comments/) : Retrieve the comments with possible use of arguments
*   [get\_approved\_comments()](https://developer.wordpress.org/reference/functions/get_approved_comments/) : Retrieve the approved comments for post id provided.
 -->

*   [`wp_list_comments()`](https://developer.wordpress.org/reference/functions/wp_list_comments/): 管理画面で設定されたパラメータを含む、さまざまな条件にもとづき、投稿または「ページ」の全コメントを表示します。
*   [`comment_form()`](https://developer.wordpress.org/reference/functions/comment_form/): 本タグは、テンプレート内で使用するための、完全なコメント・フォームを出力します。
*   [`comments_template()`](https://developer.wordpress.org/reference/functions/comments_template/): 最初の引数で指定された、コメント・テンプレートをロードします。
*   [`paginate_comments_links()`](https://developer.wordpress.org/reference/functions/paginate_comments_links/): 現在の投稿のコメントに対する、ページ送りリンクを作成します。
*   [`get_comments()`](https://developer.wordpress.org/reference/functions/get_comments/): 引数を使用して、可能であれば、コメントを取得します。
*   [`get_approved_comments()`](https://developer.wordpress.org/reference/functions/get_approved_comments/): 指定された投稿 ID の、承認済みコメントを取得します。

<!-- 
## Functions reference for retrieving comments meta
 -->

## コメント・メタを取得するための、関数リファレンス

<!-- 
*   [get\_comment\_link()](https://developer.wordpress.org/reference/functions/get_comment_link/)
*   [get\_comment\_author()](https://developer.wordpress.org/reference/functions/get_comment_author/)
*   [get\_comment\_date()](https://developer.wordpress.org/reference/functions/get_comment_date/)
*   [get\_comment\_time()](https://developer.wordpress.org/reference/functions/get_comment_time/)
*   [get\_comment\_text()](https://developer.wordpress.org/reference/functions/get_comment_text/)
 -->

*   [`get_comment_lin()`](khttps://developer.wordpress.org/reference/functions/get_comment_link/)
*   [`get_comment_author()`](https://developer.wordpress.org/reference/functions/get_comment_author/)
*   [`get_comment_date()`](https://developer.wordpress.org/reference/functions/get_comment_date/)
*   [`get_comment_time()`](https://developer.wordpress.org/reference/functions/get_comment_time/)
*   [`get_comment_text()`](https://developer.wordpress.org/reference/functions/get_comment_text/)