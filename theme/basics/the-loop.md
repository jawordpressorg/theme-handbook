<!--
# The Loop
 -->

# ループ

<!--
The Loop is the default mechanism WordPress uses for outputting posts through a theme’s [template files](https://developer.wordpress.org/themes/basics/template-files/). How many posts are retrieved is determined by the number of posts to show per page defined in the Reading settings. Within the Loop, WordPress retrieves each post to be displayed on the current page and formats it according to your theme’s instructions.
 -->

「ループ」とは、WordPress がテーマの [テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/) を通じて、投稿を出力するために使用する、デフォルトのしくみです。取得される投稿の数は、表示設定で定義された「1ページに表示する最大投稿数」によって決定されます。「ループ」内では、WordPress は、現在のページに表示される各投稿を取得し、あなたのテーマの指示に従って、フォーマットします。

<!--
The Loop extracts the data for each post from the WordPress database and inserts the appropriate information in place of each [template tag](https://developer.wordpress.org/themes/basics/template-tags/). Any HTML or PHP code in The Loop will be processed **for each post**.
 -->

「ループ」は、WordPress データベースから各投稿用のデータを抽出し、各 [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) の該当箇所に、適切な情報を挿入します。「ループ」内の HTML や PHP コードは、**各投稿に対して** 処理されます。

<!--
To put it simply, the Loop is true to its name: it loops through each post retrieved for the current page one at a time and performs the action specified in your theme.
 -->

簡単に言えば、「ループ」は、その名の通りです: 現在表示中のページ用に取得された各投稿を一つずつ順に巡回し、あなたのテーマで指定されたアクションを実行します。

<!--
You can use the Loop for a number of different things, for example to:
 -->

「ループ」は、さまざまな用途に使用でき、たとえば:

<!--
*   display post titles and excerpts on your blog’s homepage;
*   display the content and comments on a single post;
*   display the content on an individual page using template tags; and
*   display data from [Custom Post Types](https://developer.wordpress.org/themes/functionality/pages-posts-custom-post-types/) and Custom Fields.
 -->

*   あなたのブログのホームページに、投稿タイトルと抜粋を表示します;
*   個別投稿ページに、コンテンツとコメントを表示します;
*   テンプレート・タグを使用して、個別ページに、コンテンツを表示します; そして
*   [カスタム投稿タイプ](https://developer.wordpress.org/themes/functionality/pages-posts-custom-post-types/) とカスタム・フィールド由来のデータを表示します。

<!--
You can customize the Loop across your template files to display and manipulate different content.
 -->

あなたのテンプレート・ファイル全体で「ループ」をカスタマイズし、さまざまなコンテンツを表示したり操作したりできます。

<!--
## The Loop in Detail
 -->

## 「ループ」の詳細

<!--
The basic loop is:
 -->

基本ループは、次の通りです:

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

本ループは、投稿がある場合に、投稿をループ処理して表示することを示しています。より詳細に分解すると:

<!--
*   The `[have_posts()](https://developer.wordpress.org/reference/functions/have_posts/)` function checks whether there are any posts.
*   If there are posts, a **`while`** loop continues to execute as long as the condition in the parenthesis is logically true. As long as `have_posts()` continues to be true, the loop will continue.
 -->

*   `[have_posts()](https://developer.wordpress.org/reference/functions/have_posts/)` 関数は、投稿が存在するかどうかをチェックします。
*   投稿が存在する場合、**`while`** ループは、括弧内の条件が論理的に真である限り、実行を続けます。`have_posts()` が真である限り、ループは継続します。

<!--
### Using The Loop
 -->

### 「ループ」の使用

<!--
The Loop should be placed in `index.php`, and in any other templates which are used to display post information. Because you do not want to duplicate your header over and over, the loop should always be placed after the call to `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)`. For example:
 -->

「ループ」は `index.php` および、投稿情報を表示するために使用されるその他のテンプレート内に記述して、かまいません。あなたのヘッダーを繰り返し複製したくないため、ループは常に [get_header()](https://developer.wordpress.org/reference/functions/get_header/) のコール直後に記述する必要があります。たとえば:

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

上記の例では、「ループ」の終了が `endwhile` と `endif` で示されています。前述の通り、「ループ」は常に、同じ `if` および `while` 文で始まり、同じ終了文で終了しなければなりません。

<!--
Any [template tags](https://developer.wordpress.org/themes/basics/template-tags/) that you wish to apply to all posts must exist between the beginning and ending statements.
 -->

すべての投稿に適用したい任意の [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/) は、開始文と終了文の間に存在する必要があります。

<!--
You can include a custom 404 “not found” message that will be displayed if no posts matching the specified criteria are available. The message must be placed between the `endwhile` and `endif` statements, as seen in examples below.
 -->

指定した条件に合致する投稿が存在しない場合に表示される、カスタム404「見つかりません」メッセージをインクルードできます。以下の例に示すように、メッセージは `endwhile` と `endif` 文の間に記述する必要があります。

<!--
An extremely simple `index.php` file would look like:
 -->

非常にシンプルな `index.php` ファイルは、次のようになります:

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

## 「ループ」が表示できるもの

<!--
The Loop can display a number of different elements for each post. For example, some common [template tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") used in many themes are:
 -->

ループは、各投稿に対して、複数のさまざまな要素を表示できます。たとえば、多くのテーマで使用される一般的な [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") には、以下のようなものがあります:

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

*   `[next_post_link()](https://developer.wordpress.org/reference/functions/next_post_link/)` – 表示中の投稿の *後に* 公開された、投稿へのリンクです
*   `[previous_post_link()](https://developer.wordpress.org/reference/functions/previous_post_link/)` – 表示中の投稿の *前に* 公開された、投稿へのリンクです
*   `[the_category()](https://developer.wordpress.org/reference/functions/the_category/)` – 表示中の投稿またはページに関連付けられた、カテゴリーです
*   `[the_author()](https://developer.wordpress.org/reference/functions/the_author/)` – 投稿またはページの投稿者です
*   `[the_content()](https://developer.wordpress.org/reference/functions/the_content/)` – 投稿またはページにおける、メイン・コンテンツです
*   `[the_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)` – 投稿のメイン・コンテンツの最初の55語と、その後に続く省略記号 (…) または投稿全文を表示する「続きを読む」リンクです。投稿の「抜粋」フィールドを使用して、特定の抜粋の長さもカスタマイズできます。
*   `[the_ID()](https://developer.wordpress.org/reference/functions/the_id/)` – 投稿またはページの ID です
*   `[the_meta()](https://developer.wordpress.org/reference/functions/the_meta/)` – 投稿またはページに関連付けられた、カスタム・フィールドです
*   `[the_shortlink()](https://developer.wordpress.org/reference/functions/the_shortlink/)` – サイトの URL と投稿またはページの ID を使用した、ページまたは投稿へのリンクです
*   `[the_tags()](https://developer.wordpress.org/reference/functions/the_tags/)` – 投稿に関連付けられた、タグです
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – 投稿またはページの、タイトルです
*   `[the_time()](https://developer.wordpress.org/reference/functions/the_time/)` – 投稿またはページの、日付または時刻です。標準の PHP 日付関数フォーマットを使用して、カスタマイズできます。

<!--
You can also use [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/), such as:
 -->

以下のような [条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/) も使用できます:

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

*   `[is_home()](https://developer.wordpress.org/reference/functions/is_home/)` – 表示中のページが、ホームページの場合、真を返します
*   `[is_admin()](https://developer.wordpress.org/reference/functions/is_admin/)` – 管理画面内にある場合、真を、それ以外の場合、偽を返します
*   `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` – 表示中のページが、個別投稿である場合、真を返します
*   `[is_page()](https://developer.wordpress.org/reference/functions/is_page/)` – 表示中のページが、個別ページの場合、真を返します
*   `[is_page_template()](https://developer.wordpress.org/reference/functions/is_page_template/)` – ページが、特定のテンプレートを使用しているかどうかを判別するために使用できます。たとえば: `is_page_template('about-page.php')`
*   `[is_category()](https://developer.wordpress.org/reference/functions/is_category/)` – ページまたは投稿が、指定されたカテゴリーを持っている場合、真を返します。たとえば: `is_category('news')`
*   `[is_tag()](https://developer.wordpress.org/reference/functions/is_tag/)` – ページまたは投稿が、指定されたタグを持っている場合、真を返します
*   `[is_author()](https://developer.wordpress.org/reference/functions/is_author/)` – 投稿者のアーカイブ・ページ内である場合、真を返します
*   `[is_search()](https://developer.wordpress.org/reference/functions/is_search/)` – 表示中のページが、検索結果ページの場合、真を返します
*   `[is_404()](https://developer.wordpress.org/reference/functions/is_404/)` – 表示中のページが、存在しない場合、真を返します
*   `[has_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/)` – 投稿またはページに抜粋がある場合、真を返します

<!--
## Examples
 -->

## 例

<!--
Let’s take a look at some examples of the Loop in action:
 -->

「ループ」の動作例を、いくつか見てみましょう:

<!--
### Basic Examples
 -->

### 基本的な例

<!--
#### Blog Archive
 -->

#### ブログ・アーカイブ

<!--
Most blogs have a blog archive page, which can show a number of things including the post title, thumbnail, and excerpt. The example below shows a simple loop that checks to see if there are any posts and, if there are, outputs each post’s title, thumbnail, and excerpt. If no posts exists, it displays the message in parentheses.
 -->

ほとんどのブログには、投稿タイトル、サムネイル、抜粋などを表示できる、ブログ・アーカイブ・ページがあります。以下の例は、投稿が存在するかどうかを確認する単純なループを示し、投稿が存在する場合、各投稿のタイトル、サムネイル、抜粋を出力します。投稿が存在しない場合、括弧内のメッセージを表示します。

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

WordPress では、各投稿にはそれぞれ固有のページがあり、その投稿に関連する情報を表示します。テンプレート・タグを使用すると、表示したい情報をカスタマイズできます。

<!--
In the example below, the loop outputs the post’s title and content. You could use this example in a post or page template file to display the most basic information about the post. You could also customize this template to add more data to the post, for example the category.
 -->

以下の例では、ループによって、投稿のタイトルとコンテンツが出力されます。投稿や固定ページ・テンプレート・ファイルでこの例を使用すると、投稿に関する最も基本的な情報を表示できます。このテンプレートをカスタマイズして、投稿に追加データ、たとえばカテゴリーなども、追加できます。

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

### 中級レベルの例

<!--
#### Style Posts from Some Categories Differently
 -->

#### カテゴリー別に、投稿のスタイリング

<!--
The example below does a couple of things:
 -->

以下の例では、いくつかのことを行います:

<!--
*   First, it displays each post with its title, time, author, content, and category, similar to the individual post example above.
*   Next, it makes it possible for posts with the category ID of “3” to be styled differently, utilizing the `[in_category()](https://developer.wordpress.org/reference/functions/in_category/)` template tag.
 -->

*   まず、上記の個別投稿の例と同様に、各投稿をタイトル、日時、投稿者、コンテンツ、カテゴリーとともに表示します。
*   次に、`[in_category()](https://developer.wordpress.org/reference/functions/in_category/)` テンプレート・タグを利用して、カテゴリー ID が「3」の投稿を、別のスタイルで表示できるようにします。

<!--
Code comments in this example provide details throughout each stage of the loop:
 -->

本例におけるコード・コメントは、ループの各段階を通じて、詳細を提供します:

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
            // 投稿のカテゴリーをカンマで区切りで表示する
            _e( 'Posted in ', 'textdomain' ); the_category( ', ' ); 

        // "post" か "post-cat-three" のクラスが適用された div タグを閉じる
       ?>
       </div>

    <?php
    // ループを終了し、投稿が存在しない場合の処理を続ける
    endwhile; 

else :
    /*
      * 一番最初の "if" は表示できる投稿があるかどうかを確認し、
      * この "else" では投稿がなかったときの処理を行う
     */
     _e( 'Sorry, no posts matched your criteria.', 'textdomain' );

// 完全にループを終了する
 endif;
?>
```

<!--
## Multiple Loops
 -->

## 複数「ループ」

<!--
In some situations, you may need to use more than one loop. For example you may want to display the titles of the posts in a table of content list at the top of the page and then display the content further down the page. Since the query isn’t being changed we simply need to rewind the loop when we need to loop through the posts for a second time. For that we will use the function [rewind\_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/) .
 -->

状況によっては、複数のループを使用する必要が生じる場合があります。たとえば、ページ上部に目次リストとして投稿のタイトルを表示し、さらにページ下部でコンテンツを表示したい場合などです。クエリーを変更しないため、再度投稿をループ処理する必要がある場合は、ただループを巻き戻すだけで済みます。そのために [`rewind_posts()`](https://developer.wordpress.org/reference/functions/rewind_posts/) 関数を使用します。

<!--
### Using rewind\_posts
 -->

### `rewind_posts` の使用

<!--
You can use `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` to loop through the *same* query a second time. This is useful if you want to display the same query twice in different locations on a page.
 -->

*同じ* クエリーを再度ループ処理するには `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` を使用できます。ページ上の異なる場所で、同じクエリーを2回表示したい場合に、これは便利です。

<!--
Here is an example of `rewind_posts()` in use:
 -->

以下は、`rewind_posts()` の使用例です:

<!--
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
 -->

```php
<?php
// メインループを開始する
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title();
    endwhile;
endif;

// 同じクエリーを再度使うために rewind_posts() を呼び出す
rewind_posts();

// 新しいループを開始する
while ( have_posts() ) : the_post();
    the_content();
endwhile;
?>
```

<!--
### Creating secondary queries and loops
 -->

### 第二のクエリーと、第二のループの作成

<!--
Using two loops with the same query was relatively easy but not always what you will need. Instead, you will often want to create a secondary query to display different content on the template. For example, you might want to display two groups of posts on the same page, but do different things to each group. A common example of this, as shown below, is displaying a single post with a list of posts from the same category below the single post.
 -->

同じクエリーを2つのループで使用するのは比較的簡単ですが、常に必要な方法とは限りません。代わりに、テンプレート上で別のコンテンツを表示するために、第二のクエリーを作成することがよくあります。たとえば、同じページに2つの投稿グループを表示したいが、各グループでは異なる処理を行いたい場合があります。以下に示すように、この一般的な例として、個別投稿を表示し、その個別投稿の下に同じカテゴリーに由来する投稿リストを表示することが挙げられます。

<!--
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
 -->

```php
<?php
// メインクエリー
if ( have_posts() ) :
    while ( have_posts() ) : the_post();
        the_title();
        the_content();
    endwhile;
else :
    // 投稿が見つからない場合はこの文章を表示する
    _e( 'Sorry, no posts matched your criteria.' );
endif;
wp_reset_postdata();

/*
 * 2つ目のクエリー。この例では "example-category" カテゴリーの記事を取得していますが、
 * どのようなカテゴリ名でも構いません。
 */
$secondary_query = new WP_Query( 'category_name=example-category' );        

// 2つ目のループ
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

上記の例でわかるように、まず通常のループを表示します。次に、`[WP_Query](https://developer.wordpress.org/reference/classes/wp_query/)` を使用して特定のカテゴリーをクエリーする、新しい変数を定義します; この例では、`example-category` スラッグを選択しました。

<!--
Note that the regular loop in the example above has one difference: it calls `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` to reset the post data. Before you can use a second loop, you need to reset the post data. There are two ways to do this:
 -->

上記の例にある通常のループには、1つの違いがあります: 投稿データをリセットするために `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` をコールしてある点です。第二のループを使用する前に、投稿データをリセットする必要があります。これを行うには、方法が2つあります:

<!--
1.  By using the `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` function; or
2.  By creating new query objects.
 -->

1.  `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)` 関数を使用することで; または
2.  新しいクエリー・オブジェクトを作成することで。

<!--
### Resetting multiple loops
 -->

### 複数ループのリセット

<!--
It’s important when using multiple loops in a template that you reset them. Not doing so can lead to unexpected results due to how data is stored and used within the global `$post` variable. There are three main ways to reset the loop depending on the way they are called.
 -->

テンプレート内で複数ループを扱う場合、それらをリセットすることが重要です。そうしないと、グローバル変数 `$post` 内のデータの保存方法と使用方法により、予期しない結果が生じる可能性があります。コール方法に応じて、ループのリセットには、主に3つの方法があります。

<!-- 
*   `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)`
*   `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)`
*   `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)`
 -->

*   `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)`
*   `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)`
*   `[rewind_posts()](https://developer.wordpress.org/reference/functions/rewind_posts/)`

<!--
### Using wp\_reset\_postdata
 -->

### `wp_reset_postdata` の使用

<!--
Use `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` when you are running custom or multiple loops with `WP_Query`. This function restores the global `$post` variable to the current post in the main query. If you’re following best practices, this is the most common function you will use to reset loops.
 -->

カスタム・ループや複数ループを `WP_Query` で実行する際は、`[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を使用してください。本関数はグローバル変数 `$post` をメイン・クエリーの現在の投稿に復元します。ベスト・プラクティスに従う場合、これはループをリセットするために、最も頻繁に使用する関数になります。

<!--
To properly use this function, place the following code after any loops with `WP_Query`:
 -->

本関数を正しく使用するには、`WP_Query` を使用した任意のループの後に、以下のコードを記述してください:

```php
<?php wp_reset_postdata(); ?>
```

<!--
Here is an example of a loop using `WP_Query` that is reset with `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)`.
 -->

以下は、`[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` でリセットされる `WP_Query` を使用した、ループの例です。

<!--
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
 -->

```php
 <?php
// 1ページに3投稿ずつ表示するための引数
$args = array( 'posts_per_page' => 3 ); 

// WP_Query を呼び出す変数
$the_query = new WP_Query( $args ); 

if ( $the_query->have_posts() ) :
    // ループを開始する
    while ( $the_query->have_posts() ) : $the_query->the_post();
        the_title();
        the_excerpt();
    // ループを終了する
    endwhile;
else:
// このクエリーに合致する投稿がない場合には、このテキストを表示する
    _e( 'Sorry, no posts matched your criteria.', 'textdomain' );
endif; 

wp_reset_postdata();
?> 
```

<!--
### Using wp\_reset\_query
 -->

### `wp_reset_query` の使用

<!--
Using `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` restores the [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) and global `$post` data to the original main query. You **MUST** use this function to reset your loop if you use `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` within your loop. You can use it after custom loops with [WP\_Query](https://developer.wordpress.org/reference/classes/wp_query/) because it actually calls `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` when it runs. However, it’s best practice to use `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` with any custom loops involving `WP_Query`.
 -->

`[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` を使用すると、[`WP_Query`](https://developer.wordpress.org/reference/classes/wp_query/) とグローバル変数 `$post` のデータが、元のメイン・クエリーに復元されます。あなたのループ内で `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` を使用する場合、この関数を **必ず** 使用して、あなたのループをリセットしてください。実行時に実際に `[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を呼び出すため、[`WP_Query`](https://developer.wordpress.org/reference/classes/wp_query/) を使用したカスタム・ループの後でも使用できます。しかしながら、`WP_Query` を伴う任意のカスタム・ループでは、`[wp_reset_postdata()](https://developer.wordpress.org/reference/functions/wp_reset_postdata/)` を使用することが、ベスト・プラクティスです。

<!--
`[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` is *not best practice* and should be avoided if at all possible. Therefore, you shouldn’t have much use for `[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)`.
 -->

`[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)` は、*ベスト・プラクティスではない* ため、可能な限り、避けるべきです。したがって、`[wp_reset_query()](https://developer.wordpress.org/reference/functions/wp_reset_query/)` を必要とする場面は、ほとんどないはずです。

<!--
To properly use this function, place the following code after any loops with `[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/)`.
 -->

本関数を正しく使用するには、[query_posts()](https://developer.wordpress.org/reference/functions/query_posts/) を含む任意のループの後に、以下のコードを記述してください。

```php
<?php wp_reset_query(); ?>
```