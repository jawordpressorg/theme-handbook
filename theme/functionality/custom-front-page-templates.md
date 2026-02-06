<!-- 
# Custom Front Page Templates
 -->

# カスタム・ホームページ・テンプレート

<!-- 
By default, WordPress shows your most recent posts in reverse chronological order on the front page of your site. Many WordPress users want a static front page or splash page as the front page instead. This “static front page” look is common for users desiring static or welcoming information on the front page of the site.
 -->

デフォルトでは、WordPress は、あなたのサイトのホームページに、最新の投稿を時系列順に表示します。多くの WordPress ユーザーは、ホームページとして、固定のホームページやスプラッシュ・ページを希望します。この「固定ホームページ」の見た目は、サイトのホームページに、静的な情報や歓迎メッセージを表示したいユーザーに、よく見られます。

<!-- 
The look and feel of the front page of the site is based upon the choices of the user combined with the features and options of the WordPress Theme.
 -->

サイトのホームページのルック＆フィールは、ユーザーの選定内容と WordPress テーマの機能とオプションの組み合わせにもとづいています。

<!-- 
## Template Hierarchy of Custom Front Page
 -->

## カスタム・ホームページの、テンプレート階層

<!-- 
On the site front page, WordPress will always use the front-page.php template file, if it exists. If front-page.php does not exist, WordPress will determine which template file to use, depending on the user configuration of [Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") >Front page displays, as follows:
 -->

サイトのホームページに関しては、`front-page.php` テンプレート・ファイルが存在する場合には、WordPress は常にそれを使用します。`front-page.php` が存在しない場合には、WordPress は、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」のユーザー設定にもとづき、以下の順序で、どのテンプレート・ファイルを使用するかを決定します:

<!-- 
*   **A static page:** WordPress uses the [Static Page](https://codex.wordpress.org/Template_Hierarchy#Page_display "Template Hierarchy") template hierarchy:
    1.  [Custom Page Template](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates")
    2.  page-{id}.php
    3.  page-{slug}.php
    4.  page.php
    5.  index.php
*   **Your latest posts:** WordPress uses the [Blog Posts Index](https://codex.wordpress.org/Template_Hierarchy#Home_Page_display "Template Hierarchy") template hierarchy:
    1.  home.php
    2.  index.php
 -->

*   **固定ページ:** WordPress は [固定ページ](https://codex.wordpress.org/Template_Hierarchy#Page_display "Template Hierarchy") テンプレート階層を使用します:
    1.  [カスタム・ページ・テンプレート](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates")
    2.  `page-{id}.php`
    3.  `page-{slug}.php`
    4.  `page.php`
    5.  `index.php`
*   **最新の投稿:** WordPress は [ブログ投稿インデックス](https://codex.wordpress.org/Template_Hierarchy#Home_Page_display "Template Hierarchy") テンプレート階層を使用します:
    1.  `home.php`
    2.  `index.php`

<!-- 
### Custom Site Front Page Template
 -->

### カスタム・サイト・ホームページ・テンプレート

<!-- 
To create a custom site front page template, include either of the following in the Theme:
 -->

カスタム・サイト・ホームページ・テンプレートを作成するには、「テーマ」に以下のいずれかをインクルードしてください:

<!-- 
*   front-page.php
*   A [Custom Page Template](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates") (e.g. template-featured.php for featured content)
 -->

*   `front-page.php`
*   [カスタム・ページ・テンプレート](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates") (例: 注目コンテンツ用の `template-featured.php`)

<!-- 
### Custom Blog Posts Index Page Template
 -->

### カスタム・ブログ投稿インデックスページ・テンプレート

<!-- 
To create a custom blog posts index template, include the following in the Theme:
 -->

カスタム・ブログ投稿インデックス・テンプレートを作成するには、「テーマ」に以下をインクルードしてください:

<!-- 
*   home.php
 -->

*   `home.php`

<!-- 
Use only the home.php template file for the blog posts index. Do not use a Custom Page Template (such as template-blog.php) for two reasons:
 -->

ブログ投稿インデックス用としては、`home.php` テンプレート・ファイルのみを使用します。カスタム・ページ・テンプレート (`template-blog.php` など) を使用しない理由は、2つあります:

<!-- 
1.  When the static front page feature is configured properly, WordPress will not use a Custom Page Template to display the blog posts index, even if a Custom Page Template is assigned to the page designated as the “Posts page”. WordPress will *only* use either home.php or index.php.
2.  When the Custom Page Template is assigned to a static page other than the one designated as the “Posts page,” the blog posts index loop pagination will not work properly.
 -->

1.  固定ホームページ機能が正しく設定されている場合、WordPress は、カスタム・ページ・テンプレートが、「投稿ページ」として指定されたページに適用されていたとしても、ブログ投稿インデックスの表示に、カスタム・ページ・テンプレートを使用しません。WordPress は、`home.php` または `index.php` のいずれか *のみ* を使用します。
2.  カスタム・ページ・テンプレートが、「投稿ページ」として指定されたページ以外の固定ページに適用されている場合、ブログ投稿インデックス・ループのページネーションが、正常に機能しません。

<!-- 
## Contextual Conditional Tags
 -->

## コンテキスト条件付きタグ

<!-- 
### is\_front\_page
 -->

### `is_front_page`

<!-- 
The [Conditional Tag](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page) checks if the site front page is being displayed. Returns true when the site front page is being displayed, regardless of whether ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts” or “A static page”.
 -->

[条件付きタグ](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [`is_front_page()`](https://codex.wordpress.org/Function_Reference/is_front_page) は、サイトのホームページが表示されているか否かをチェックします。サイトのホームページが表示されている場合、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」が「最新の投稿」または「固定ページ」のいずれに設定されていても、真を返します。

<!-- 
### is\_home
 -->

### `is_home`

<!-- 
The [Conditional Tag](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [is\_home()](https://codex.wordpress.org/Function_Reference/is_home) checks if the blog posts index is being displayed. Returns true when the blog posts index is being displayed: when the site front page is being displayed and ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts”, or when ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “A static page” and the “Posts Page” value is the current [Page](https://codex.wordpress.org/Pages "Pages") being displayed.
 -->

[条件付きタグ](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [`is_home()`](https://codex.wordpress.org/Function_Reference/is_home) は、ブログ投稿インデックスが表示されているか否かをチェックします。ブログ投稿インデックスが表示されている場合に、真を返します: サイトのホームページが表示されており、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」が「最新の投稿」に設定されている場合、または「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」が「固定ページ」に設定され、「投稿ページ」の値が現在 [ページ](https://codex.wordpress.org/Pages "Pages") として表示されている場合。

<!-- 
When the site front page is being displayed and ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts”, both[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/) and [is\_home()](https://developer.wordpress.org/reference/functions/is_home/) will return true.
 -->

サイトのホームページが表示されており、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」が「最新の投稿」に設定されている場合、[`is_front_page()`](https://developer.wordpress.org/reference/functions/is_front_page/) と [`is_home()`](https://developer.wordpress.org/reference/functions/is_home/) の両方が真を返します。

<!-- 
## Configuration of front-page.php
 -->

## `front-page.php` の設定

<!-- 
If it exists, the front-page.php template file is used on the site’s front page regardless of whether ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “A static page” or “Your latest posts,” the Theme will need to account for both options, so that the site front page will display either a static page or the blog posts index. There are a few methods to do so.
 -->

`front-page.php` テンプレート・ファイルが存在する場合、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」が「固定ページ」または「最新の投稿」のいずれに設定されているかに関係なく、サイトのホームページに関しては、`front-page.php` テンプレート・ファイルが使用されるので、「テーマ」では両方のオプションに対応する必要があるため、サイトのホームページは固定ページまたはブログ投稿インデックスのどちらでも表示できるようにします。これを行う方法はいくつかあります。

<!-- 
### Conditional display within front-page.php
 -->

### `front-page.php` 内での、条件付き表示

<!-- 
One way to allow front-page.php to account for both options for ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is to add a conditional inside of front-page.php itself, using [get\_option( 'show\_on\_front' )](https://codex.wordpress.org/Option_Reference#Reading "Option Reference"), [get\_home\_template()](https://codex.wordpress.org/Function_Reference/get_home_template "Function Reference/get home template"), and[get\_page\_template()](https://codex.wordpress.org/Function_Reference/get_page_template "Function Reference/get page template").
 -->

「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > ホームページの表示」の2つのオプションを `front-page.php` が処理できる様にする方法の一つは、`front-page.php` 自身の内部に、[`get_option('show_on_front')`](https://codex.wordpress.org/Option_Reference#Reading "Option Reference")、[`get_home_template()`](https://codex.wordpress.org/Function_Reference/get_home_template "Function Reference/get home template") および [`get_page_template()`](https://codex.wordpress.org/Function_Reference/get_page_template "Function Reference/get page template") を用いた条件分岐を追加することです。

<!-- 
Method 1: including custom content directly within front-page.php:  
 -->

方法1: `front-page.php` 内にカスタム・コンテンツを、直接インクルードします:  

```php
if ( 'posts' == get_option( 'show_on_front' ) ) {
    include( get_home_template() );
} else {
    // Custom content markup goes here
}
```

<!-- 
Method 2: including any page template:  
 -->

方法2: 任意のページ・テンプレートを、インクルードします:  

```php
if ( 'posts' == get_option( 'show_on_front' ) ) {
    include( get_home_template() );
} else {
    include( get_page_template() );
}
```

<!-- 
### Filtering frontpage\_template
 -->

### `frontpage_template` のフィルタリング

<!-- 
Another way to allow the site front page to display either a static page/custom content or the blog posts index, without adding conditional code within front-page.php, is to [filter frontpage\_template](https://codex.wordpress.org/Function_Reference/get_query_template "Function Reference/get query template"), by adding a filter callback to functions.php:  
 -->

サイトのホームページに、固定ページ/カスタム・コンテンツまたはブログ投稿インデックスを表示させる、もう一つの方法としては、`front-page.php` 内に条件付きコードを追加せずに、`functions.php` にフィルター・コールバックを追加することで、[`frontpage_template` のフィルタリング](https://codex.wordpress.org/Function_Reference/get_query_template "Function Reference/get query template") を行う方法があります:  

```php
function themeslug_filter_front_page_template( $template ) {
    return is_home() ? '' : $template;
}
add_filter( 'frontpage_template', 'themeslug_filter_front_page_template' );
```

<!-- 
This method causes WordPress to bypass the front-page.php template file altogether when the blog posts index is being displayed.
 -->

このメソッドは、ブログ投稿インデックスが表示される際に、WordPress が `front-page.php` テンプレート・ファイルを完全にバイパスするようにします。

<!-- 
## Adding custom query loops to front-page.php
 -->

## `front-page.php` に、カスタム・クエリー・ループの追加

<!-- 
If the front-page.php template file includes a default [WordPress Loop](https://codex.wordpress.org/The_Loop "The Loop"), like so:  
 -->

`front-page.php` テンプレート・ファイルにデフォルト [WordPress「ループ」](https://codex.wordpress.org/The_Loop "The Loop") を含む場合、以下のようにします:  

```php
&lt;?php
if ( have_posts() ) : while ( have_posts() ) : the_post();
    // do something
endwhile; else:
    // no posts found
endif;
```

<!-- 
That loop applies to the post content of the static page assigned to ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Posts page’.
 -->

そのループは、「[設定](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [表示設定](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") > 投稿ページ」に割り当てられた固定ページの投稿コンテンツに適用されます。

<!-- 
To display custom loops (latest blog posts, custom/featured content, etc.), add secondary loop queries using calls to [WP\_Query](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query"). For example, to show the 3 latest blog posts:  
 -->

カスタム・ループ (最新のブログ投稿、カスタム/注目のコンテンツなど) を表示するには、[`WP_Query`](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query") をコールして、二次ループ・クエリーを追加します。たとえば、最新のブログ投稿3件を表示するには:  

```php
$latest_blog_posts = new WP_Query( array( 'posts_per_page' =&gt; 3 ) );

if ( $latest_blog_posts-&gt;have_posts() ) : while ( $latest_blog_posts-&gt;have_posts() ) : $latest_blog_posts-&gt;the_post();
    // Loop output goes here
endwhile; endif;
```

<!-- 
## Pagination
 -->

## ページネーション

<!-- 
Static front pages are not intended to be paged. None of the WordPress [Previous / Next page link](https://codex.wordpress.org/Next_and_Previous_Links "Next and Previous Links") functions work with a static front page. Pagination on a static front page uses the page query variable, not the paged variable. See the [WP\_Query](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query") for details.
 -->

固定ホームページは、ページネーションを想定して設計されていません。WordPress の [「前 / 次」ページ・リンク](https://codex.wordpress.org/Next_and_Previous_Links "Next and Previous Links") 関数は、固定ホームページでは一切機能しません。固定ホームページでのページネーションには、`paged` 変数ではなく `page` クエリー変数を使用します。詳細は [`WP_Query`](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query") をご覧ください。