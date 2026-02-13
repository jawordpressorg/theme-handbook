<!-- 
# Pagination
 -->

# ページネーション

<!-- 
Pagination allows your user to *page* back and forth through multiple pages of content.
 -->

ページネーションにより、あなたのユーザーは、コンテンツの複数ページを *ページ* 単位で前後に移動できます。

<!-- 
WordPress can use pagination when:
 -->

WordPress は、次の場合にページネーションを使用できます:

<!-- 
*   Viewing lists of posts when more posts exist than can fit on one page, or
*   Breaking up longer posts by manually by using the following tag: `<!--nextpage-->`
 -->

*   投稿のリストを表示する際に、1ページに表示できる投稿数を超える投稿が存在する場合、あるいは
*   右記のタグ `<!--nextpage-->` を使用して、長文の投稿を手動で分割する場合

<!-- 
## Using Pagination to Navigate Post Lists
 -->

## 投稿リストのナビゲーションに、ページネーションの使用

<!-- 
The most common use for pagination in WordPress sites is to break up long lists of posts into separate pages. Whether you’re viewing a category, archive, or default index page for a blog or site, WordPress only shows 10 posts per page by default. Users can change the number of posts that appear on each page on the Reading screen: **Admin > Settings > Reading**.
 -->

WordPress サイトにおける、ページネーションの最も一般的な用途は、長い投稿リストを別々のページに分割することです。あなたがブログやサイトのカテゴリー、アーカイブ、もしくはデフォルトの index ページを表示する場合、WordPress は、デフォルトで1ページあたり10件の投稿のみを表示します。ユーザーは、**管理画面 > 設定 > 表示設定** 画面で、各ページに表示される投稿数を変更できます。

<!-- 
## Examples
 -->

## 例

<!-- 
### Loop with Pagination
 -->

### ページネーションを伴う、ループ

<!-- 
This simplified example shows where you can add pagination functions for the main loop. Add the functions just before or after the loop.
 -->

簡略化された本例は、メインループに於けるページネーション関数を追加できる箇所を示しています。関数は、ループの直前または直後に追加しましょう。

```php
<?php if ( have_posts() ) : ?>

    <!-- Start the pagination functions before the loop. -->
    <div class="nav-previous alignleft"><?php next_posts_link( 'Older posts' ); ?></div>
    <div class="nav-next alignright"><?php previous_posts_link( 'Newer posts' ); ?></div>
    <!-- End the pagination functions before the loop. -->

	<!-- Start of the main loop. -->
	<?php while ( have_posts() ) : the_post();  ?>

	<!-- the rest of your theme's main loop -->

    <?php endwhile; ?>
    <!-- End of the main loop -->

    <!-- Start the pagination functions after the loop. -->
    <div class="nav-previous alignleft"><?php next_posts_link( 'Older posts' ); ?></div>
    <div class="nav-next alignright"><?php previous_posts_link( 'Newer posts' ); ?></div>
    <!-- End the pagination functions after the loop. -->

<?php else : ?>

	<?php _e( 'Sorry, no posts matched your criteria.' ); ?>

<?php endif; ?>
```

<!-- 
### Methods for displaying pagination links
 -->

### ページネーションリンクの表示に関する、メソッド

<!-- 
When using any of these pagination functions outside the template file with the loop that is being paginated, you must call the global variable $wp\_query.
 -->

これらのページネーション関数のいずれかを、ページネーション対象のループを伴うテンプレートファイル外で使用する場合、必ずグローバル変数 `$wp_query` をコールする必要があります。

```php
function your_themes_pagination() {
	global $wp_query;
	echo paginate_links();
}
```

<!-- 
WordPress has numerous functions for displaying links to other pages in your loop. Some of these functions are only used in very specific contexts. You would use a different function on a single post page then you would on a archive page. The following section covers archive template pagination functions. The section after that cover single post pagination.
 -->

WordPress には、あなたのループ内で他ページへのリンクを表示するための、数多くの関数があります。これらの関数のいくつかは、非常に限定された状況でのみ使用されます。個別投稿ページで使用する関数は、アーカイブページで使用する関数とは、異なります。以降のセクションでは、アーカイブテンプレートのページネーション関数について取り上げます。その先のセクションでは、個別投稿のページネーションについて取り上げます。

<!-- 
#### Simple Pagination
 -->

#### シンプルな、ページネーション

<!-- 
**posts\_nav\_link**
 -->

**`posts_nav_link`**

<!-- 
One of the simplest methods is [posts\_nav\_link()](https://developer.wordpress.org/reference/functions/posts_nav_link/). Simply place the function in your template after your loop. This generates both links to the next page of posts and previous page of posts where applicable. This function is ideal for themes that have simple pagination requirements.
 -->

最もシンプルなメソッドの一つは [`posts_nav_link()`](https://developer.wordpress.org/reference/functions/posts_nav_link/) です。あなたのテンプレート内の、あなたのループの後に、この関数を記述するだけです。適用可能な場合、投稿の次ページと前ページへのリンクの両方を生成します。本関数は、シンプルなページネーション要件を持つテーマに最適です。

```php
posts_nav_link();
```

<!-- 
**next\_posts\_link & prev\_posts\_link**
 -->

**`next_posts_link` & `prev_posts_link`**

<!-- 
When building a theme, use [next\_posts\_link()](https://developer.wordpress.org/reference/functions/next_posts_link/) and [prev\_posts\_link()](https://developer.wordpress.org/reference/functions/previous_posts_link/). to have control over where the previous and next posts page link appears.
 -->

テーマを作成する際は、[`next_posts_link()`](https://developer.wordpress.org/reference/functions/next_posts_link/) と [`prev_posts_link()`](https://developer.wordpress.org/reference/functions/previous_posts_link/) を使用して、前の投稿ページと次の投稿ページへのリンクが表示される位置を制御しましょう。

```php
next_posts_link();
previous_posts_link();
```

<!-- 
If you need to pass the pagination links to a PHP variable, you can use [get\_next\_posts\_link()](https://developer.wordpress.org/reference/functions/get_next_posts_link/) and [get\_previous\_posts\_link()](https://developer.wordpress.org/reference/functions/get_previous_posts_link/).
 -->

ページネーション・リンクを PHP 変数に渡す必要がある場合は、[`get_next_posts_link()`](https://developer.wordpress.org/reference/functions/get_next_posts_link/) および [`get_previous_posts_link()`](https://developer.wordpress.org/reference/functions/get_previous_posts_link/) を使用できます。

```php
$next_posts = get_next_posts_link();
$prev_posts = get_previous_posts_link();
```

<!-- 
#### Numerical Pagination
 -->

#### 数字ページネーション

<!-- 
When you have many pages of content it is a better experience to display a list of page numbers so the user can click on any one of the page links rather then having to repeatedly click next or previous posts. WordPress provides several functions for automatically displaying a numerical pagination list.
 -->

コンテンツのページ数が多い場合、ページ番号のリストを表示するほうがユーザー体験が向上し、これにより、ユーザーは「次へ」や「前へ」を繰り返しクリックする代わりに、任意のページリンクをクリックできます。WordPress では、数字ページネーション・リストを自動的に表示するための、複数の関数が提供されています。

<!-- 
**For WordPress 4.1+**
 -->

**WordPress v4.1以降向け**

<!-- 
If you want more robust pagination options, you can use [the\_posts\_pagination()](https://developer.wordpress.org/reference/functions/the_posts_pagination/) for WordPress 4.1 and higher. This will output a set of page numbers with links to previous and next pages of posts.
 -->

より堅牢なページネーション・オプションが必要な場合、WordPress v4.1以降では [`the_posts_pagination()`](https://developer.wordpress.org/reference/functions/the_posts_pagination/) を使用できます。これにより、投稿の前後ページへのリンク付きページ番号のセットが出力されます。

```php
the_posts_pagination();
```

<!-- 
**For WordPress prior to 4.1**
 -->

**WordPress v4.1以前向け**

<!-- 
If you want your pagination to support older versions of WordPress, you must use [paginate\_links()](https://developer.wordpress.org/reference/functions/paginate_links/).
 -->

WordPress の古いバージョンでも、あなたのページネーションをサポートしたい場合、[`paginate_links()`](https://developer.wordpress.org/reference/functions/paginate_links/) を使用する必要があります。

```php
echo paginate_links();
```

<!-- 
#### Pagination Between Single Posts
 -->

#### 個別投稿間の、ページネーション

<!-- 
All of the previous functions should be used on index and archive pages. When you are viewing a single blog post, you must use [prev\_post\_link](https://developer.wordpress.org/reference/functions/previous_post_link/) and [next\_post\_link](https://developer.wordpress.org/reference/functions/next_post_link/). Place the following functions below the loop on your single.php.
 -->

上記のすべての関数は、index ページおよびアーカイブページで使用する必要があります。個別ブログ投稿を表示する際は、[`prev_post_link`](https://developer.wordpress.org/reference/functions/previous_post_link/) と [`next_post_link`](https://developer.wordpress.org/reference/functions/next_post_link/) を使用しなければなりません。あなたの `single.php` のループ直下に、以下の関数を配置しましょう。

```php
previous_post_link();
next_post_link();
```

<!-- 
### Pagination within a post
 -->

### 投稿内の、ページネーション

<!-- 
WordPress gives you a tag that can be placed in post content to enable pagination for that post:  
`<!--nextpage-->`  
If you use that tag in the content, you need to ensure that the [wp\_link\_pages](https://developer.wordpress.org/reference/functions/wp_link_pages/) function is placed in your single.php template within the loop.
 -->

WordPress では、投稿コンテンツ内に配置することでその投稿のページネーションを有効化するタグ `<!--nextpage-->` を提供しています。このタグをコンテンツ内で使用する場合、あなたの `single.php` テンプレートのループ内に、[`wp_link_pages`](https://developer.wordpress.org/reference/functions/wp_link_pages/) 関数が配置されていることを確認する必要があります。

```php
<?php if ( have_posts() ) : ?>

	<!-- Start of the main loop. -->
	<?php while ( have_posts() ) : the_post(); ?>

		<?php the_content(); ?>

		<?php wp_link_pages(); ?>

	<?php endwhile; ?>
	<!-- End of the main loop. -->

<?php endif; ?>
```