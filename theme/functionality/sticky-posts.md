<!-- 
# Sticky Posts
 -->

# 固定投稿

<!-- 
A Sticky Post is the post will be placed at the top of the front page of posts. This feature is only available for the built-in post type post and not for custom post types.
 -->

「固定投稿」とは、投稿のホームページの上部に配置される、投稿です。この機能は、ビルトインの投稿タイプ「投稿」でのみ利用可能であり、カスタム投稿タイプでは利用できません。

<!-- 
## How to stick a post
 -->

## 投稿の固定方法

<!-- 
1.  Go to **Administration Screen > Posts > Add New** or **Edit**
2.  In the right side menu, Click Edit link of Visibility option in Publish group
3.  Click Stick this post to the front page option
 -->

1.  **管理画面 > 投稿 > 新規追加** または **編集** に移動します。
2.  右側のメニューで、公開設定グループ内の「表示設定」リンクをクリックします。
3.  「この投稿を先頭に固定表示」オプションをクリックします。

<!-- 
![](https://i0.wp.com/developer.wordpress.org/files/2017/01/sticked_post.jpg?resize=307%2C449&ssl=1)
 -->

![](https://i0.wp.com/developer.wordpress.org/files/2017/01/sticked_post.jpg?resize=307%2C449&ssl=1)

<!-- 
## Display Sticky Posts
 -->

## 「固定投稿」の表示

<!-- 
### Show Sticky Posts
 -->

### 「固定投稿」を表示

<!-- 
Display just the first sticky post. At least one post must be designated as a “sticky post” or else the loop will display all posts:
 -->

最初の固定投稿のみを表示します。少なくとも1つの投稿を「固定投稿」として指定する必要があり、さもなければ、ループはすべての投稿を表示します:

```php
<?php
$sticky = get_option( 'sticky_posts' );
$query  = new WP_Query( 'p=' . $sticky[0] );
```

<!-- 
Display just the first sticky post, if none return the last post published:
 -->

最初の固定投稿のみを表示し、存在しない場合は、最後にされた投稿を表示します:

```php
<?php
$args  = array(
	'posts_per_page'      => 1,
	'post__in'            => get_option( 'sticky_posts' ),
	'ignore_sticky_posts' => 1,
);
$query = new WP_Query( $args );
```

<!-- 
Display just the first sticky post, if none return nothing:
 -->

最初の固定投稿のみを表示し、存在しない場合は、何も返しません:

```php
<?php
$args   = array(
	'posts_per_page'      => 1,
	'post__in'            => get_option( 'sticky_posts' ),
	'ignore_sticky_posts' => 1,
);
$query  = new WP_Query( $args );
if ( isset( $sticky[0] ) ) {
	// Insert here your stuff...
}
```

<!-- 
### Don’t Show Sticky Posts
 -->

### 「固定投稿」を非表示

<!-- 
Exclude all sticky posts from the query:
 -->

クエリーから、すべての固定投稿を、除外します:

```php
<?php
$args  = array( 'post__not_in' => get_option( 'sticky_posts' ) );
$query = new WP_Query( $args );
```

<!-- 
Exclude sticky posts from a category. Return ALL posts within the category, but don’t show sticky posts at the top. The ‘sticky posts’ will still show in their natural position (e.g. by date):
 -->

カテゴリーから、固定投稿を除外します。カテゴリー内の全投稿を返しますが、固定投稿を先頭に表示しません。「固定投稿」は、元の位置 (たとえば、日付順) に表示されます:

```php
<?php
$args  = array(
	'ignore_sticky_posts' => 1,
	'posts_per_page'      => 3,
	'cat'                 => 6,
);
$query = new WP_Query( $args );
```

<!-- 
Exclude sticky posts from a category. Return posts within the category, but exclude sticky posts completely, and adhere to paging rules:
 -->

カテゴリーから、固定投稿を除外します。カテゴリー内の投稿を返しますが、固定投稿は完全に除外し、ページングルールに従います:

```php
<?php
$args  = array(
	'cat'                 => 3,
	'ignore_sticky_posts' => 1,
	'post__not_in'        => get_option( 'sticky_posts' ),
	'paged'               => get_query_var( 'paged' ) ? get_query_var( 'paged' ) : 1,
);
$query = new WP_Query( $args );
```

<!-- 
Use get\_query\_var( ‘page’ ) if you want this query to work in a Page template that you’ve set as your static front page.
 -->

あなたの固定ホームページとしてセットした「ページ」テンプレートで、このクエリーを動作させたい場合は、`get_query_var('page')` を使用しましょう。

```php
<?php
/* Get all Sticky Posts */
$sticky = get_option( 'sticky_posts' );

/* Sort Sticky Posts, newest at the top */
rsort( $sticky );

/* Get top 5 Sticky Posts */
$sticky = array_slice( $sticky, 0, 5 );

/* Query Sticky Posts */
$query = new WP_Query( array(
	'post__in'            => $sticky,
	'ignore_sticky_posts' => 1,
) );
```

<!-- 
## Style Sticky Posts
 -->

## 「固定投稿」のスタイリング

<!-- 
To help theme authors perform simpler styling, the [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) function is used to add class=”…” to DIV, just add:
 -->

テーマ作者がシンプルにスタイリングできるように、[`post_class()`](https://developer.wordpress.org/reference/functions/post_class/) 関数を使って、`div` に `class="…"` をただ追加しましょう:

```php
<div id="post-<?php the_ID(); ?>" <?php post_class(); ?>>
```

<!-- 
The [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) outputs the class=”whatever” piece for that div. This includes several different classes of value: post, hentry (for hAtom microformat pages), category-X (where X is the slug of every category the post is in), and tag-X (similar, but with tags). It also adds “sticky” for posts marked as Sticky Posts.
 -->

[`post_class()`](https://developer.wordpress.org/reference/functions/post_class/) は、その `div` 要素に対して `class="whatever"` の部分を出力します。これにはさまざまな値のクラスが含まれます: `post`、`hentry` (`hAtom` マイクロフォーマットページ用)、`category-X` (`X` は、当該投稿が属する各カテゴリーのスラッグ)、`tag-X` (同様だがタグ用)。また、「固定投稿」としてマークされた投稿には、`sticky` も追加されます。

```css
.sticky { color: red; }
```

<!-- 
The “sticky” class is only added for sticky posts on the first page of the home page ([is\_home()](https://developer.wordpress.org/reference/functions/is_home/) is true and [is\_paged()](https://developer.wordpress.org/reference/functions/is_paged/) is false)
 -->

`sticky` クラスは、ホームページの最初のページ ([`is_home()`](https://developer.wordpress.org/reference/functions/is_home/) が真で、[`is_paged()`](https://developer.wordpress.org/reference/functions/is_paged/) が偽) 上の固定投稿にのみ、追加されます。