<!--
# The Loop
-->
# ループ

<!--
The Loop is the default mechanism WordPress uses for outputting posts through a theme’s [template files](https://developer.wordpress.org/themes/basics/template-files/). How many posts are retrieved is determined by the number of posts to show per page defined in the Reading settings. Within the Loop, WordPress retrieves each post to be displayed on the current page and formats it according to your theme’s instructions.
-->
ループは、テーマの[テンプレートファイル](https://developer.wordpress.org/themes/basics/template-files/)の中で投稿を表示する際に使用する WordPress のしくみです。1ページに表示する投稿の数は、管理画面の表示設定の中で設定できます。ループ内では、現在のページに表示するべき投稿を取得し、テーマの実装に沿って投稿をフォーマットします。

<!--
The Loop extracts the data for each post from the WordPress database and inserts the appropriate information in place of each [template tag](https://developer.wordpress.org/themes/basics/template-tags/). Any HTML or PHP code in The Loop will be processed **for each post**.
-->
ループは WordPress のデータベースから各投稿のデータを取得し、[テンプレートタグ](https://developer.wordpress.org/themes/basics/template-tags/)の位置に適切な情報を挿入します。ループ内の HTML や PHP のコードは**各投稿ごとに**実行されます。

<!--
To put it simply, the Loop is true to its name: it loops through each post retrieved for the current page one at a time and performs the action specified in your theme.
-->
簡単に言うと、ループでは現在のページで取得した投稿に対して、1つずつテーマで指定されたアクションを実行します。

<!--
You can use the Loop for a number of different things, for example to:
-->
ループは次のような様々な用途で使用できます:

<!--
*   display post titles and excerpts on your blog’s homepage;
*   display the content and comments on a single post;
*   display the content on an individual page using template tags; and
*   display data from [Custom Post Types](https://developer.wordpress.org/themes/functionality/pages-posts-custom-post-types/) and Custom Fields.
-->
*   ブログのホームページで投稿のタイトルや抜粋を表示する
*   投稿のコンテンツやコメントを表示する
*   テンプレートタグを使ってコンテンツを個別のページに表示する
*   [カスタム投稿タイプ](https://developer.wordpress.org/themes/functionality/pages-posts-custom-post-types/)やカスタムフィールドのデータを表示する

<!--
You can customize the Loop across your template files to display and manipulate different content.
-->
テンプレートファイルの中でループをカスタマイズすると、さまざまなコンテンツを表示したり操作できます。

<!--
## The Loop in Detail
-->
## ループの詳細

<!--
The basic loop is:
-->
ループの基本的な形は次の通りです:

```php
<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        // Display post content
    endwhile;
endif;
?>
```

<!--
This loop says that when there are posts, loop through and display the posts. Broken down into more detail:
-->
このループは、投稿があればループして投稿内容を表示する例です。さらに詳しく見て見ましょう:

<!--
*   The `[have_posts()](https://developer.wordpress.org/reference/functions/have_posts/)` function checks whether there are any posts.
*   If there are posts, a **`while`** loop continues to execute as long as the condition in the parenthesis is logically true. As long as `have_posts()` continues to be true, the loop will continue.
-->
*   `[have_posts()](https://developer.wordpress.org/reference/functions/have_posts/)` 関数で投稿が存在するかを確認しています。
*   もし投稿がある場合は、括弧内の条件が論理的に真である限り、 **`while`** ループが実行されます。つまり、 `have_posts()` が真である限り、ループが継続します。

<!--
### Using The Loop
-->
### ループの使い方

<!--
The Loop should be placed in `index.php`, and in any other templates which are used to display post information. Because you do not want to duplicate your header over and over, the loop should always be placed after the call to `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)`. For example:
-->
ループは `index.php` や、投稿の内容を表示するためのテンプレートの中で使う必要があります。ヘッダーを何度も重複させたくないので、ループは常に `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` の後で呼び出すべきです。

```php
<?php
get_header();
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        // Display post content
    endwhile;
endif;
?>
```

<!--
In the above example, the end of the Loop is shown with an `endwhile` and `endif`. The Loop must always begin with the same `if` and `while` statements, as mentioned above and must end with the same end statements.
-->
上記の例では、ループの終わりに `endwhile` と `endif` があります。ループは常に同じ `if` 文と `while` 文で始まり、同じ end 文で終わらなければなりません。

<!--
Any [template tags](https://developer.wordpress.org/themes/basics/template-tags/) that you wish to apply to all posts must exist between the beginning and ending statements.
-->
すべての投稿に適用したい[テンプレートタグ](https://developer.wordpress.org/themes/basics/template-tags/)は、開始文と終了文の間に記述する必要があります。

<!--
Tip: You can include a custom 404 “not found” message that will be displayed if no posts matching the specified criteria are available. The message must be placed between the `endwhile` and `endif` statements, as seen in examples below.
-->
ヒント: 条件に合致する投稿がない場合に、独自の404「見つかりませんでした」のメッセージを表示できます。次の例のように、このメッセージは `endwhile` と `endif` の間に記述する必要があります。

<!--
An extremely simple `index.php` file would look like:
-->
簡単な `index.php` ファイルは次のようになります:

```php
<?php
get_header();

if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_content();
    endwhile;
else :
    _e( 'Sorry, no posts matched your criteria.', 'textdomain' );
endif;

get_sidebar();
get_footer();
?>
```

<!--
## What the Loop Can Display
-->
## ループで表示できるもの

<!--
The Loop can display a number of different elements for each post. For example, some common [template tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") used in many themes are:
-->
ループでは、投稿ごとに多くの要素を表示できます。たとえば、一般的に使える[テンプレートタグ](https://developer.wordpress.org/themes/basics/template-tags/)は次の通りです:

<!--
*   `[next_post_link()](https://developer.wordpress.org/reference/functions/next_post_link/)` – a link to the post published chronologically *after* the current post
*   `[previous_post_link()](https://developer.wordpress.org/reference/functions/previous_post_link/)` – a link to the post published chronologically *before* the current post
*   `[the_category()](https://developer.wordpress.org/reference/functions/the_category/)` – the category or categories associated with the post or page being viewed
*   `[the_author()](https://developer.wordpress.org/reference/functions/the_author/)` – the author of the post or page
*   `[the_content()](https://developer.wordpress.org/reference/functions/the_content/)` – the main content for a post or page
*   `[the_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)` – the first 55 words of a post’s main content followed by an ellipsis (…) or read more link that goes to the full post. You may also use the “Excerpt” field of a post to customize the length of a particular excerpt.
*   `[the_ID()](https://developer.wordpress.org/reference/functions/the_id/)` – the ID for the post or page
*   `[the_meta()](https://developer.wordpress.org/reference/functions/the_meta/)` – the custom fields associated with the post or page
*   `[the_shortlink()](https://developer.wordpress.org/reference/functions/the_shortlink/)` – a link to the page or post using the url of the site and the ID of the post or page
*   `[the_tags()](https://developer.wordpress.org/reference/functions/the_tags/)` – the tag or tags associated with the post
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – the title of the post or page
*   `[the_time()](https://developer.wordpress.org/reference/functions/the_time/)` – the time or date for the post or page. This can be customized using standard php date function formatting.
-->
*   `[next_post_link()](https://developer.wordpress.org/reference/functions/next_post_link/)` – 現在の投稿の**後**に公開された投稿へのリンク
*   `[previous_post_link()](https://developer.wordpress.org/reference/functions/previous_post_link/)` – 現在の投稿の**前**に公開された投稿へのリンク
*   `[the_category()](https://developer.wordpress.org/reference/functions/the_category/)` – 表示している投稿や固定ページに関連するカテゴリー
*   `[the_author()](https://developer.wordpress.org/reference/functions/the_author/)` – 投稿や固定ページの投稿者
*   `[the_content()](https://developer.wordpress.org/reference/functions/the_content/)` – 投稿や固定ページのコンテンツ
*   `[the_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)` – 投稿のコンテンツの最初の55文字と省略記号 (…)、または、投稿に遷移するためのリンク。投稿の「抜粋」フィールドを使って抜粋の長さをカスタマイズできます。
*   `[the_ID()](https://developer.wordpress.org/reference/functions/the_id/)` – 投稿や固定ページの ID
*   `[the_meta()](https://developer.wordpress.org/reference/functions/the_meta/)` – 投稿や固定ページに関連するカスタムフィールド
*   `[the_shortlink()](https://developer.wordpress.org/reference/functions/the_shortlink/)` – サイトの URL と投稿や固定ページの ID を使って生成する、投稿や固定ページへのリンク
*   `[the_tags()](https://developer.wordpress.org/reference/functions/the_tags/)` – 投稿に関連するタグ
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – 投稿や固定ページのタイトル
*   `[the_time()](https://developer.wordpress.org/reference/functions/the_time/)` – 投稿や固定ページの日付や時刻。php の標準の date 関数のフォーマットを使ってカスタマイズできます。

<!--
You can also use [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/), such as:
-->
[条件分岐タグ](https://developer.wordpress.org/themes/basics/conditional-tags/)を使うこともできます:

<!--
*   `[is_home()](https://developer.wordpress.org/reference/functions/is_home/)` – Returns true if the current page is the homepage
*   `[is_admin()](https://developer.wordpress.org/reference/functions/is_admin/)` – Returns true if inside Administration Screen, false otherwise
*   `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` – Returns true if the page is currently displaying a single post
*   `[is_page()](https://developer.wordpress.org/reference/functions/is_page/)` – Returns true if the page is currently displaying a single page
*   `[is_page_template()](https://developer.wordpress.org/reference/functions/is_page_template/)` – Can be used to determine if a page is using a specific template, for example: `is_page_template('about-page.php')`
*   `[is_category()](https://developer.wordpress.org/reference/functions/is_category/)` – Returns true if page or post has the specified category, for example: `is_category('news')`
*   `[is_tag()](https://developer.wordpress.org/reference/functions/is_tag/)` – Returns true if a page or post has the specified tag
*   `[is_author()](https://developer.wordpress.org/reference/functions/is_author/)` – Returns true if inside author’s archive page
*   `[is_search()](https://developer.wordpress.org/reference/functions/is_search/)` – Returns true if the current page is a search results page
*   `[is_404()](https://developer.wordpress.org/reference/functions/is_404/)` – Returns true if the current page does not exist
*   `[has_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/)` – Returns true if the post or page has an excerpt
-->
*   `[is_home()](https://developer.wordpress.org/reference/functions/is_home/)` – 現在のページがホームページであれば true を返す
*   `[is_admin()](https://developer.wordpress.org/reference/functions/is_admin/)` – 管理画面であれば true を返す
*   `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` – 個別投稿を表示していれば true を返す
*   `[is_page()](https://developer.wordpress.org/reference/functions/is_page/)` – 固定ページを表示していれば true を返す
*   `[is_page_template()](https://developer.wordpress.org/reference/functions/is_page_template/)` – 固定ページが任意のテンプレートを使用しているか判断します。例: `is_page_template('about-page.php')`
*   `[is_category()](https://developer.wordpress.org/reference/functions/is_category/)` – 指定されたカテゴリーのアーカイブページを表示していれば true を返す。例: `is_category('news')`
*   `[is_tag()](https://developer.wordpress.org/reference/functions/is_tag/)` – 指定されたタグのアーカイブページを表示していれば true を返す
*   `[is_author()](https://developer.wordpress.org/reference/functions/is_author/)` – 投稿者のアーカイブページを表示していれば true を返す
*   `[is_search()](https://developer.wordpress.org/reference/functions/is_search/)` – 検索ページを表示していれば true を返す
*   `[is_404()](https://developer.wordpress.org/reference/functions/is_404/)` – 現在のページが存在しなければ true を返す
*   `[has_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/)` – 投稿や固定ページに抜粋があれば true を返す

<!--
## Examples
-->
## 例

<!--
Let’s take a look at some examples of the Loop in action:
-->
ループの使い方を見てみましょう:

<!--
### Basic Examples
-->
### 基本的な例

<!--
#### Blog Archive
-->
#### ブログアーカイブ

<!--
Most blogs have a blog archive page, which can show a number of things including the post title, thumbnail, and excerpt. The example below shows a simple loop that checks to see if there are any posts and, if there are, outputs each post’s title, thumbnail, and excerpt. If no posts exists, it displays the message in parentheses.
-->
多くのブログには投稿タイトル、サムネイル、抜粋を表示するブログアーカイブページがあります。次の例は、投稿があるかをチェックし、投稿がある場合にはそれぞれの投稿のタイトル、サムネイル、抜粋を表示するループの例です。投稿がない場合は、括弧の中のメッセージを表示します。

```php
<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title( '<h2>', '</h2>' );
        the_post_thumbnail();
        the_excerpt();
    endwhile;
else:
    _e( 'Sorry, no posts matched your criteria.', 'textdomain' );
endif;
?>
```

<!--
#### Individual Post
-->
#### 個別の投稿

<!--
In WordPress, each post has its own page, which displays the relevant information for that post. Template tags allow you to customize which information you want to display.
-->
WordPress の投稿には個別のページがあり、関連する情報が表示されます。テンプレートタグを使って表示する情報をカスタマイズできます。

<!--
In the example below, the loop outputs the post’s title and content. You could use this example in a post or page template file to display the most basic information about the post. You could also customize this template to add more data to the post, for example the category.
-->
以下のループの例では、投稿のタイトルとコンテンツを表示します。投稿や固定ページのテンプレートファイルで使うと、投稿に関する基本的な情報を表示できます。このテンプレートをカスタマイズすれば、カテゴリーといったより多くのデータを投稿に追加できます。

```php
<?php
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title( '<h1>', '</h1>' );
        the_content();
    endwhile;
else:
    _e( 'Sorry, no pages matched your criteria.', 'textdomain' );
endif;
?>
```

<!--
### Intermediate Examples
-->
### 発展的な使い方

<!--
#### Style Posts from Some Categories Differently
-->
#### カテゴリーに応じてスタイルを変更する

<!--
The example below does a couple of things:
-->
以下の例ではいくつかのことを行います:

<!--
*   First, it displays each post with its title, time, author, content, and category, similar to the individual post example above.
*   Next, it makes it possible for posts with the category ID of “3” to be styled differently, utilizing the `[in_category()](https://developer.wordpress.org/reference/functions/in_category/)` template tag.
-->
*   まず、上記の例と同様に、各投稿のタイトル、時刻、投稿者、コンテンツ、カテゴリーを表示します。
*   次に、 `[in_category()](https://developer.wordpress.org/reference/functions/in_category/)` テンプレートタグを使って、カテゴリー ID が "3" の投稿に異なる装飾を適用します。

<!--
Code comments in this example provide details throughout each stage of the loop:
-->
この例のコード内のコメントで、ループの各段階ごとに解説しています。

<!--
```php
<?php
// Start the Loop.
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        /* * See if the current post is in category 3.
          * If it is, the div is given the CSS class "post-category-three".
          * Otherwise, the div is given the CSS class "post".
        */
        if ( in_category( 3 ) ) : ?>
        <div class="post-category-three">
        <?php else : ?>
        <div class="post">
        <?php endif; 

            // Display the post's title.
            the_title( '<h2>', ';</h2>' ); 

            // Display a link to other posts by this posts author.
            printf( __( 'Posted by %s', 'textdomain' ), get_the_author_posts_link() );

            // Display the post's content in a div.
            ?>
            <div class="entry">
                <?php the_content() ?>
             </div>

            <?php
            // Display a comma separated list of the post's categories.
            _e( 'Posted in ', 'textdomain' ); the_category( ', ' ); 

        // closes the first div box with the class of "post" or "post-cat-three"
       ?>
       </div>

    <?php
    // Stop the Loop, but allow for a "if not posts" situation
    endwhile; 

else :
    /*
      * The very first "if" tested to see if there were any posts to
      * display. This "else" part tells what do if there weren't any.
     */
     _e( 'Sorry, no posts matched your criteria.', 'textdomain' );

// Completely stop the Loop.
 endif;
?>
```
-->

```php
<?php
// ループを開始する
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        /* * 投稿のカテゴリ ID が 3 の場合、
          * div に "post-category-three" クラスを適用し、
          * それ以外の場合は "post" クラスを適用する
        */
        if ( in_category( 3 ) ) : ?>
        <div class="post-category-three">
        <?php else : ?>
        <div class="post">
        <?php endif; 

            // 投稿のタイトルを表示する
            the_title( '<h2>', ';</h2>' ); 

            // この投稿者のその他の投稿へのリンクを表示する
            printf( __( 'Posted by %s', 'textdomain' ), get_the_author_posts_link() );

            // 投稿のコンテンツを div タグ内で表示する
            ?>
            <div class="entry">
                <?php the_content() ?>
             </div>

            <?php
            // 投稿のカテゴリをカンマで区切りで表示する
            _e( 'Posted in ', 'textdomain' ); the_category( ', ' ); 

        // "post" か "post-cat-three" のクラスが適用された div タグを閉じる
       ?>
       </div>

    <?php
    // ループを終了し、投稿が存在しない場合の処理を続ける
    endwhile; 

else :
    /*
      * 一番最初の "if" は表示できる投稿があるかどうかを確認します。
      * この "else" では投稿がなかったときの処理をします。
     */
     _e( 'Sorry, no posts matched your criteria.', 'textdomain' );

// 完全にループを終了する
 endif;
?>
```

<!--
## Multiple Loops
-->
## 複数のループ

<!--
In some situations, you may need to use more than one loop. For example you may want to display the titles of the posts in a table of content list at the top of the page and then display the content further down the page. Since the query isn’t being changed we simply need to rewind the loop when we need to loop through the posts for a second time. For that we will use the function [rewind\_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/) .
-->
場合によって、複数のループを使う必要があるかもしれません。たとえば、ページ上部で投稿のタイトルを表に表示し、ページ下部でコンテンツを表示することがあるかもしれません。クエリーは変更されないため、投稿を2回目にループする場合はループを巻き戻す必要があります。その際は [rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/) 関数を使います。

<!--
### Using rewind\_posts
-->
### rewind_posts を使う

<!--
You can use `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` to loop through the *same* query a second time. This is useful if you want to display the same query twice in different locations on a page.
-->
`[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` を使うと、**同じ**クエリーを2回ループさせることができます。同じクエリーをページの異なる箇所に使いたい場合に有用です。

<!--
Here is an example of `rewind_posts()` in use:
-->
`rewind_posts()` の例です:

```php
<?php
// Start the main loop
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title();
    endwhile;
endif;

// Use rewind_posts() to use the query a second time.
rewind_posts();

// Start a new loop
while ( have_posts() ) : the_post();
    the_content();
endwhile;
?>
```

<!--
### Creating secondary queries and loops
-->
### 2つ目のクエリーとループを使う

<!--
Using two loops with the same query was relatively easy but not always what you will need. Instead, you will often want to create a secondary query to display different content on the template. For example, you might want to display two groups of posts on the same page, but do different things to each group. A common example of this, as shown below, is displaying a single post with a list of posts from the same category below the single post.
-->
同じクエリーでループを2つ使うのは簡単ですが、必ずしもそれが求めているものであるとは限りません。しばしば、テンプレートの中で異なるコンテンツを表示するために2つ目のクエリーを作りたいでしょう。たとえば、同じページの中で2つのグループの投稿を表示して、それぞれのグループで異なる処理をする場合です。よくある使い方は、以下のように、投稿のコンテンツの下に同じカテゴリーに属する投稿のリストを表示することです。

```php
<?php
// The main query.
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title();
        the_content();
    endwhile;
else :
    // When no posts are found, output this text.
    _e( 'Sorry, no posts matched your criteria.' );
endif;
wp_reset_postdata();                                                        

/*
 * The secondary query. Note that you can use any category name here. In our example,
 * we use "example-category".
 */
$secondary_query = new WP_Query( 'category_name=example-category' );        

// The second loop.
if ( $secondary_query->have_posts() )
    echo '<ul>';
    while ( $secondary_query->have_posts() ) : $secondary_query->the_post();
        the_title( '<li>', '</li>' );
     endwhile;
     echo '</ul>';
endif;
wp_reset_postdata();
?>
```

<!--
As you can see in the example above, we first display a regular loop. Then we define a new variable that uses `[WP_Query](https://developer.wordpress.org/reference/classes/wp_query/)` to query a specific category; in our case, we chose the `example-category` slug.
-->
上記の例では、まず通常のループを表示します。次に、特定のカテゴリー (上記の例では `example-category` のスラッグ) を取得するため `[WP_Query](https://developer.wordpress.org/reference/classes/wp_query/)` を使って新しい変数を定義します。

<!--
Note that the regular loop in the example above has one difference: it calls `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` to reset the post data. Before you can use a second loop, you need to reset the post data. There are two ways to do this:
-->
上記の例で、通常のループとは異なる点が1つあります。それは、 `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を呼び出して投稿データをリセットしている点です。2つ目のループを使う前に、投稿データをリセットする必要があります。これには2通りの方法があります:

<!--
1.  By using the `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` function; or
2.  By creating new query objects.
-->
1.  `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` 関数を使う
2.  新しいクエリーオブジェクトを作る

<!--
### Resetting multiple loops
-->
### 複数のループをリセットする

<!--
It’s important when using multiple loops in a template that you reset them. Not doing so can lead to unexpected results due to how data is stored and used within the global `$post` variable. There are three main ways to reset the loop depending on the way they are called.
-->
テンプレートの中で複数のループを使う際に、それらをリセットすることが重要です。そうしないと、グローバル変数の `$post` 内でどのようにデータを保存し使用するかによって、予期しない結果となることがあります。呼び出し方に応じて、ループをリセットする方法が3通りあります。

*   `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)`
*   `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)`
*   `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)`

<!--
### Using wp\_reset\_postdata
-->
### wp_reset_postdata を使う

<!--
Use `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` when you are running custom or multiple loops with `WP_Query`. This function restores the global `$post` variable to the current post in the main query. If you’re following best practices, this is the most common function you will use to reset loops.
-->
`WP_Query` を使ってカスタムループや複数のループを実行する際は `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を使ってください。この関数はグローバル変数の `$post` の内容をメインクエリーの投稿のものにリストアします。これはループをリセットする際に最もよく使う関数です。

<!--
To properly use this function, place the following code after any loops with `WP_Query`:
-->
この関数を適切に使うには、次のコードを `WP_Query` を使ったループの後に記述します:

```php
<?php wp_reset_postdata(); ?>
```

<!--
Here is an example of a loop using `WP_Query` that is reset with `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)`.
-->
以下は `WP_Query` を使ったループを `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` でリセットする例です。

```php
 <?php
// Example argument that defines three posts per page.
$args = array( 'posts_per_page' => 3 ); 

// Variable to call WP_Query.
$the_query = new WP_Query( $args ); 

if ( $the_query->have_posts() ) :
    // Start the Loop
    while ( $the_query->have_posts() ) : $the_query->the_post();
        the_title();
        the_excerpt();
    // End the Loop
    endwhile;
else:
// If no posts match this query, output this text.
    _e( 'Sorry, no posts matched your criteria.', 'textdomain' );
endif; 

wp_reset_postdata();
?> 
```

<!--
### Using wp\_reset\_query
-->
### wp_reset_query を使う

<!--
Using `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` restores the [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) and global `$post` data to the original main query. You **MUST** use this function to reset your loop if you use `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` within your loop. You can use it after custom loops with [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) because it actually calls `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` when it runs. However, it’s best practice to use `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` with any custom loops involving `WP_Query`.
-->
`[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` を使うと、 [WP_Query](https://developer.wordpress.org/reference/classes/wp_query/) とグローバル変数の `$post` データを元のメインループのクエリにリストアできます。ループの中で `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` を使った場合は、この関数を使ってループを**必ず**リセットする必要があります。この関数は裏で `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` が実行されるので、 [WP_Query](https://developer.wordpress.org/reference/classes/wp_query/) を使ったカスタムループの後でこの関数を使うこともできます。ただし、 `WP_Query` が関係するループでは `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を使うことが推奨されています。

<!--
Alert: `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` is *not best practice* and should be avoided if at all possible. Therefore, you shouldn’t have much use for `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)`.
-->
注意: `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` は**推奨されておらず**、可能な限り避けてください。そのため、 `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` を使う機会も少ないでしょう。

<!--
To properly use this function, place the following code after any loops with `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)`.
-->
この関数を適切に使うには、 `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` を使ったループの後に次のコードを記述してください。

```php
<?php wp_reset_query(); ?>
```
