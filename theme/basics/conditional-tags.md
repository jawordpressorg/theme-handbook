<!-- 
# Conditional Tags
 -->

# 条件タグ

<!-- 
Conditional Tags can be used in your Template Files in classic themes to alter the display of content depending on the conditions that the current page matches. They tell WordPress what code to display under specific conditions. Conditional Tags usually work with PHP [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") Conditional Statements.
 -->

「条件タグ」は、クラシック・テーマのあなたの「テンプレート・ファイル」内で使用でき、現在のページが一致する条件に応じてコンテンツの表示を変更します。これらは特定の条件下で、どのコードを表示するかを WordPress に指示します。条件タグは通常、PHP の [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional")「条件文」と連携して動作します。

<!-- 
The code begins by checking to see **if** a statement is true or false. If the statement is found to be true, the first set of code is executed. If it’s false, the first set of code is skipped, and the second set of code (after the **else**) is executed instead.
 -->

コードはまず **if** 文が真か偽かを判定します。文が真と判定された場合、最初のコード群が実行されます。偽の場合、最初のコード群はスキップされ、代わりに (**else** 以降の) 2番目のコード群が実行されます。

<!-- 
For example, you could ask if a user is logged in, and then provide a different greeting depending on the result.
 -->

たとえば、ユーザーがログインしているかどうかを尋ね、その結果に応じて異なる挨拶を提供できます。

```php
if ( is_user_logged_in() ) :
	echo 'Welcome, registered user!';
else :
	echo 'Welcome, visitor!';
endif;
```

<!-- 
Note the close relation these tags have to [WordPress Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).
 -->

これらのタグが [WordPress テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/) と密接に関連していることに注意してください。

<!-- 
## Where to Use Conditional Tags
 -->

## 条件タグの使用箇所

<!-- 
For a Conditional Tag to modify your data, the information must already have been retrieved from your database, i.e. the query must have already run. If you use a Conditional Tag before there is data, there’ll be nothing to ask the if/else statement about.
 -->

「条件付きタグ」であなたのデータを変更するには、その情報はすでにデータベースから取得済みである必要があります。つまり、クエリーはすでに実行済みでなければなりません。データが存在しない状態で「条件付きタグ」を使用すると、if/else 文が判断する対象が存在しなくなります。

<!-- 
It’s important to note that WordPress loads `functions.php` before the query is run, so if you simply include a Conditional Tag in that file, it won’t work.
 -->

重要な点として、WordPress はクエリーが実行される前に `functions.php` を読み込むため、単にそのファイルに「条件タグ」を含めても機能しません。

<!-- 
Two ways to implement Conditional Tags:
 -->

「条件付きタグ」を実装する2つの方法とは:

<!-- 
*   place it in a [Template File](https://developer.wordpress.org/themes/basics/template-files/)
*   create a function out of it in `functions.php` that hooks into an action/filter that triggers at a later point
 -->

*   [テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/) に記述する
*   後でトリガーされるアクション/フィルターにフックする関数を `functions.php` 内に、作成する

<!-- 
## The Conditions For
 -->

## 条件

<!-- 
Listed below are the conditions under which each of the following **conditional statements proves to be true**. Tags which can accept parameters are noted.
 -->

以下に、**条件文が真となる** 各条件を列挙します。パラメータを使用可能なタグは、注記されています。

<!-- 
### The Main Page
 -->

### メイン・ページ

<!-- 
[is\_home()](https://developer.wordpress.org/reference/functions/is_home/ "Function_Reference/is_home")
 -->

[is\_home()](https://developer.wordpress.org/reference/functions/is_home/ "Function_Reference/is_home")

<!-- 
This condition returns true when the main blog page is being displayed, usually in standard reverse chronological order. If your home page has been set to a Static Page instead, then this will only prove true on the page which you set as the “Posts page” in Settings > Reading.
 -->

この条件は、メインのブログページが表示されている場合に真を返します。ブログページは通常標準的な、投稿の新しい順で表示されます。あなたのホームページが代わりに「静的ページ」に設定されている場合、この条件が真となるのは、「設定 > 表示設定」で「投稿ページ」として設定したページのみに限定されます。

<!-- 
### The Front Page
 -->

### フロント・ページ

<!-- 
[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/ "Function_Reference/is_front_page")
 -->

[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/ "Function_Reference/is_front_page")

<!-- 
This condition returns true when the front page of the site is displayed, regardless of whether it is set to show posts or a static page.
 -->

この条件は、サイトのフロントページが表示される場合に真を返し、投稿を表示するか静的ページを表示するかにかかわらず適用されます。

<!-- 
Returns true when:
 -->

次の場合に、真を返します:

<!-- 
1.  the main blog page is being displayed **and**
2.  the Settings > Reading -> *Front page displays* option is set to *Your latest posts*
 -->

1.  メイン・ブログページが表示され、**かつ**
2.  「設定 > 表示設定 -> *ホームページの表示*」オプションが *最新の投稿* に設定されている

<!-- 
**OR**
 -->

**または**

<!-- 
1.  when Settings > Reading -> *Front page displays* is set to *A static page* **and**
2.  the Front Page value is the current Page being displayed.
 -->

1.  「設定 > 表示設定 -> *ホームページの表示*」オプションが *固定ページ* に設定され、**かつ**
2.  「ホームページ」の値が、現在表示されている「ページ」である

<!-- 
### The Administration Panels
 -->

### 管理パネル

<!-- 
[is\_admin()](https://developer.wordpress.org/reference/functions/is_admin/ "Function_Reference/is_admin")
 -->

[is\_admin()](https://developer.wordpress.org/reference/functions/is_admin/ "Function_Reference/is_admin")

<!-- 
This condition returns true when the Dashboard or the administration panels are being displayed.
 -->

この条件は、「ダッシュボード」または管理パネルが表示されている場合に、真を返します。

<!-- 
### A Single Post Page
 -->

### 個別投稿ページ

<!-- 
[is\_single()](https://developer.wordpress.org/reference/functions/is_single/ "Function_Reference/is_single")
 -->

[is\_single()](https://developer.wordpress.org/reference/functions/is_single/ "Function_Reference/is_single")

<!-- 
Returns true when any single Post (or attachment, or custom Post Type) is being displayed. This condition returns false if you are on a page.
 -->

任意の「個別投稿」(または添付ファイル、「カスタム投稿タイプ」) が表示されている場合に、真を返します。固定ページを表示している場合、この条件は偽を返します。

```php
is_single( '17' );
```

<!-- 
[is\_single()](https://developer.wordpress.org/reference/functions/is_single/) can also check for certain posts by ID and other parameters. The above example proves true when Post 17 is being displayed as a single Post.
 -->

[is\_single()](https://developer.wordpress.org/reference/functions/is_single/) は、ID やその他のパラメータによって、特定の投稿をチェックできます。上記の例は、「投稿」17が「個別投稿」として表示されている場合に、真になります。

```php
is_single( 'Irish Stew' );
```

<!-- 
Parameters include Post titles, as well. In this case, it proves true when the Post with title “Irish Stew” is being displayed as a single Post.
 -->

パラメータには「投稿タイトル」も含まれます。この場合、「Irish Stew」というタイトルの「投稿」が「個別投稿」として表示されているときに、真になります。

```php
is_single( 'beef-stew' );
```

<!-- 
Proves true when the Post with Post Slug “beef-stew” is being displayed as a single Post.
 -->

「投稿スラッグ」が「beef-stew」である「投稿」が「個別投稿」として表示されている場合に、真になります。

```php
is_single( array( 17, 'beef-stew', 'Irish Stew' ) );
```

<!-- 
Returns true when the single post being displayed is either post ID 17, or the post\_name is “beef-stew”, or the post\_title is “Irish Stew”.
 -->

表示されている個別投稿の投稿 ID が 17、または `post_name` が「beef-stew」、または `post_title` が「Irish Stew」のいずれかに該当する場合に、真を返します。

```php
is_single( array( 17, 19, 1, 11 ) );
```

<!-- 
Returns true when the single post being displayed is either post ID = 17, post ID = 19, post ID = 1 or post ID = 11.
 -->

表示されている個別投稿が、投稿 ID = 17、投稿 ID = 19、投稿 ID = 1、または投稿 ID = 11のいずれかである場合に、真を返します。

```php
is_single( array( 'beef-stew', 'pea-soup', 'chilli' ) );
```

<!-- 
Returns true when the single post being displayed is either the post\_name “beef-stew”, post\_name “pea-soup” or post\_name “chilli”.
 -->

表示されている個別投稿が、`post_name`「beef-stew」、`post_name`「pea-soup」、または `post_name`「chilli」のいずれかである場合に、真を返します。

```php
is_single( array( 'Beef Stew', 'Pea Soup', 'Chilli' ) );
```

<!-- 
Returns true when the single post being displayed is either the post\_title is “Beef Stew”, post\_title is “Pea Soup” or post\_title is “Chilli”.
 -->

表示されている個別投稿が、`post_title` が「ビーフシチュー」、`post_title` が「エンドウ豆のスープ」、または `post_title` が「チリ」のいずれかである場合に、真を返します。

<!-- 
Note: This function does not distinguish between the post ID, post title, or post name. A post named “17” would be displayed if a post ID of 17 was requested. Presumably the same holds for a post with the slug “17”.
 -->

注: この関数は投稿 ID、投稿タイトル、投稿名などを区別しません。投稿 ID が17の投稿をリクエストした場合、「17」という投稿名が表示されます。おそらくスラッグが「17」の投稿についても、同様の挙動となります。

<!-- 
### A Single Post, Page, or Attachment
 -->

### 個別投稿、ページ、または添付ファイル

<!-- 
[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)
 -->

[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)

<!-- 
Returns true for any is\_single, is\_page, and is\_attachment. It does allow testing for post types.
 -->

`is_single`、`is_page`、`is_attachment` のいずれに対しても、真を返します。投稿タイプのテストは可能です。

<!-- 
### A Sticky Post
 -->

### 固定投稿

<!-- 
[is\_sticky()](https://developer.wordpress.org/reference/functions/is_sticky/ "Function_Reference/is_sticky")
 -->

[is\_sticky()](https://developer.wordpress.org/reference/functions/is_sticky/ "Function_Reference/is_sticky")

<!-- 
Returns true if the “Stick this post to the front page” check box has been checked for the current post. In this example, no post ID argument is given, so the post ID for the Loop post is used.
 -->

現在の投稿に対して「この投稿を先頭に固定表示」チェックボックスがチェックされている場合、真を返します。この例では投稿 ID 引数が指定されていないため、ループ投稿の投稿 ID が使用されます。

```php
is_sticky( '17' );
```

<!-- 
Returns true when Post 17 is considered a sticky post.
 -->

「投稿」17が固定表示と見なされる場合に、真を返します。

<!-- 
### A Post Type
 -->

### 投稿タイプ

<!-- 
[get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/ "Function_Reference/get_post_type")
 -->

[get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/ "Function_Reference/get_post_type")

<!-- 
You can test to see if the current post is of a certain type by including [get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/ "Function Reference/get_post_type") in your conditional. It’s not really a conditional tag, but it returns the [registered post type](https://developer.wordpress.org/reference/functions/register_post_type/ "Function Reference/Register Post Type") of the current post.
 -->

現在の投稿が特定のタイプかどうかを確認するには、あなたの条件式に [`get_post_type()`](https://developer.wordpress.org/reference/functions/get_post_type/ "Function Reference/get_post_type") を含めることでテストできます。これは厳密には条件タグではありませんが、現在の投稿の [登録済み投稿タイプ](https://developer.wordpress.org/reference/functions/register_post_type/ "Function Reference/Register Post Type") を返します。

```php
if ( 'book' == get_post_type() ) { ... }
```

<!-- 
[post\_type\_exists()](https://developer.wordpress.org/reference/functions/post_type_exists/ "Function Reference/post_type_exists")
 -->

[post\_type\_exists()](https://developer.wordpress.org/reference/functions/post_type_exists/ "Function Reference/post_type_exists")

<!-- 
Returns true if a given post type is a registered post type. This does not test if a post is a certain post\_type. Note: This function replaces a function called is\_post\_type which existed briefly in 3.0 development.
 -->

指定された投稿タイプが登録済み投稿タイプである場合に、真を返します。これは投稿が特定の `post_type` であるかどうかをテストするものではありません。注: この関数は、v3.0開発中に短期間存在した `is_post_type` 関数に代わるものです。

<!-- 
### A Post Type is Hierarchical
 -->

### 投稿タイプは階層構造

<!-- 
[is\_post\_type\_hierarchical( $post\_type )](https://developer.wordpress.org/reference/functions/is_post_type_hierarchical/ "Function-reference/is_post_type_hierarchical/")
 -->

[is\_post\_type\_hierarchical( $post\_type )](https://developer.wordpress.org/reference/functions/is_post_type_hierarchical/ "Function-reference/is_post_type_hierarchical/")

<!-- 
Returns true if this $post\_type has been set with hierarchical support when registered.
 -->

この `$post_type` が登録時に階層サポート付きで設定されている場合、真を返します。

```php
 is_post_type_hierarchical( 'book' );
```

<!-- 
Returns true if the book post type was registered as having support for hierarchical.
 -->

投稿タイプ「書籍」が階層構造をサポートするように登録されている場合、真を返します。

<!-- 
###  A Post Type Archive
 -->

###  投稿タイプのアーカイブ

<!-- 
[is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/ "Function_Reference/is_post_type_archive")
 -->

[is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/ "Function_Reference/is_post_type_archive")

<!-- 
Returns true on any post type archive.
 -->

すべての投稿タイプのアーカイブで、真を返します。

```php
is_post_type_archive( $post_type );
```

<!-- 
Returns true if on a post type archive page that matches $post\_type (can be a single post type or an array of post types).
 -->

`$post_type` (個別投稿タイプ、または投稿タイプの配列) に一致する投稿タイプのアーカイブページの場合に、真を返します。

<!-- 
To turn on post type archives, use ‘has\_archive’ => true, when [registering the post type](https://make.wordpress.org/docs/plugin-developer-handbook/9-custom-post-types-and-taxonomies/registering-custom-post-types/ "Function_Reference/register_post_type").
 -->

投稿タイプのアーカイブを有効にするには、[投稿タイプの登録](https://make.wordpress.org/docs/plugin-developer-handbook/9-custom-post-types-and-taxonomies/registering-custom-post-types/ "Function_Reference/register_post_type") 時に、「has\_archive」=> true を使用してください。

<!-- 
### Any Page Containing Posts
 -->

### 投稿を含む任意のページ

<!-- 
[comments\_open()](https://developer.wordpress.org/reference/functions/comments_open/ "Function_Reference/comments_open")
 -->

[comments\_open()](https://developer.wordpress.org/reference/functions/comments_open/ "Function_Reference/comments_open")

<!-- 
When comments are allowed for the current Post being processed in the [WordPress Loop](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/the-loop/ "The Loop").
 -->

[WordPress ループ](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/the-loop/ "The Loop") 内で処理中の現在の投稿に対して、コメントが許可されている場合。

<!-- 
[pings\_open()](https://developer.wordpress.org/reference/functions/pings_open/ "Function_Reference/pings_open")
 -->

[pings\_open()](https://developer.wordpress.org/reference/functions/pings_open/ "Function_Reference/pings_open")

<!-- 
When pings are allowed for the current Post being processed in the WordPress Loop.
 -->

WordPress ループ内で処理中の投稿に対して、ping が許可されている場合。

<!-- 
### A “PAGE” Page
 -->

### 「PAGE」ページ

<!-- 
This section refers to WordPress Pages, not any generic webpage from your blog, or in other words to the built in *post\_type* ‘page’.
 -->

本セクションは WordPress「ページ」を指しており、あなたのブログの一般的な Web ページ、あるいは言い換えればビルトインの *`post_type`*「page」を指すものではありません。

<!-- 
[is\_page()](https://developer.wordpress.org/reference/functions/is_page/ "Function_Reference/is_page")
 -->

[is\_page()](https://developer.wordpress.org/reference/functions/is_page/ "Function_Reference/is_page")

<!-- 
When any Page is being displayed.
 -->

任意の「ページ」が表示されている場合。

```php
is_page( '42' );
```

<!-- 
When Page 42 (ID) is being displayed.
 -->

「ページ」42 (ID) が表示されている場合。

```php
is_page( 'About Me And Joe' );
```

<!-- 
When the Page with a *post\_title* of “About Me And Joe” is being displayed.
 -->

「About Me And Joe」という *`post_title`* を持つ「ページ」が表示されている場合。

```php
is_page( 'about-me' );
```

<!-- 
When the Page with a *post\_name* (slug) of “about-me” is being displayed.
 -->

「about-me」という *`post_name`* (スラッグ) を持つ「ページ」が表示されている場合。

```php
is_page( array( 42, 'about-me', 'About Me And Joe' ) );
```

<!-- 
Returns true when the Pages displayed is either *post ID* = 42, or *post\_name* is “about-me”, or *post\_title* is “About Me And Joe”.
 -->

表示されている「ページ」が *post ID* = 42、または *`post_name`* が「about-me」、または *`post_title`* が「About Me And Joe」のいずれかに該当する場合、真を返します。

```php
is_page( array( 42, 54, 6 ) );
```

<!-- 
Returns true when the Pages displayed is either *post ID* = 42, or *post ID* = 54, or *post ID* = 6.
 -->

表示されている「ページ」が *post ID* = 42、または *post ID* = 54、または *post ID* = 6のいずれかに該当する場合、真を返します。

<!-- 
#### Testing for Paginated Pages
 -->

#### ページ・ネーションされたページのテスト

<!-- 
You can use this code to check whether you’re on the nth page in a Post or Page that has been divided into pages using the `<!--nextpage-->` QuickTag. This can be useful, for example, if you wish to display meta-data only on the first page of a post divided into several pages.
 -->

このコードを使用すると、`<!--nextpage-->`「クイックタグ」でページ分割された「投稿」や「ページ」において、現在 n 番目のページを表示しているかどうかを確認できます。たとえば、複数ページに分割された投稿の最初のページのみに、メタデータを表示したい場合などに便利です。

<!-- 
##### Example 1
 -->

##### 例1

```php
<?php
$paged = $wp_query->get( 'page' );
if ( ! $paged || $paged < 2 ) :
	// This is not a paginated page (or it's simply the first page of a paginated page/post)
else :
	// This is a paginated page.
endif;
```

<!-- 
##### Example 2
 -->

##### 例2

```php
<?php
$paged = get_query_var( 'page' ) ? get_query_var( 'page' ) : false;
if ( $paged == false ) :
	// This is not a paginated page (or it's simply the first page of a paginated page/post)
else :
	// This is a paginated page.
endif;
```

<!-- 
#### Testing for Sub-Pages
 -->

#### サブ・ページのテスト

<!-- 
There is no `is_subpage()` function, but you can test this with a little code:
 -->

`is_subpage()` 関数は存在しませんが、少しコードを書けばこれをテストできます:

```php
<?php
global $post; // if outside the loop

if ( is_page() && $post->post_parent ) :
	// This is a subpage
else :
	// This is not a subpage
endif;
```

<!-- 
**Snippet 1**
 -->

**スニペット1**

<!-- 
You can create your own is\_subpage() function using the code in Snippet 2. Add it to your functions.php file. It tests for a parent page in the same way as Snippet 1, but will return the ID of the page parent if there is one, or false if there isn’t.
 -->

スニペット2のコードを使用して、独自の `is_subpage()` 関数を作成できます。あなたの functions.php ファイルに追加しましょう。この関数はスニペット1と同様に親ページを判定しますが、親ページが存在する場合にその ID を返し、存在しない場合は偽を返します。

<!-- 
**Snippet 2**
 -->

**スニペット2**

```php
<?php
function is_subpage() {
	// Load details about this page.
	global $post;

	// Test to see if the page has a parent
	if ( is_page() && $post->post_parent ) {
		// return the ID of the parent post
		return $post->post_parent;

	// there is no parent so ...
	} else {
		// ... the answer to the question is false
		return false;
	}
}
```

<!-- 
It is advisable to use a function like that in Snippet 2, rather than using the simple test like Snippet 1, if you plan to test for sub-pages frequently.
 -->

サブページを頻繁にテストする予定がある場合は、スニペット1のような単純なテストではなく、スニペット2のような関数を使用することをおすすめします。

<!-- 
To test if the parent of a page is a specific page, for instance “About” (page id pid 2 by default), we can use the tests in Snippet 3. These tests check to see if we are looking at the page in question, as well as if we are looking at any child pages. This is useful for setting variables specific to different sections of a web site, so a different banner image, or a different heading.
 -->

ページの親が特定のページ、たとえば「About」(デフォルトでは、ページ id pid は2) であるかどうかをテストするには、スニペット3のテストを使用できます。これらのテストは、対象のページを表示しているか、またその子ページを表示しているかを確認します。これは、Web サイトの異なるセクションごとに固有の変数を設定するのに有用で、たとえば、異なるバナー画像や異なる見出しを表示する場合などに活用できます。

<!-- 
**Snippet 3**
 -->

**スニペット3**

```php
<?php
// The page is "About", or the parent of the page is "About".
if ( is_page( 'about' ) || '2' == $post->post_parent ) {
	$bannerimg = 'about.jpg';
} elseif ( is_page( 'learning' ) || '56' == $post->post_parent ) {
	$bannerimg = 'teaching.jpg';
} elseif ( is_page( 'admissions' ) || '15' == $post->post_parent ) {
	$bannerimg = 'admissions.jpg';
// Just in case we are at an unclassified page, perhaps the home page
} else {
	$bannerimg = 'home.jpg';
}
```

<!-- 
Snippet 4 is a function that allows you to carry out the tests above more easily. This function will return true if we are looking at the page in question (so “About”) or one of its sub pages (so a page with a parent with ID “2”).
 -->

スニペット4は、上記のテストをより簡単に実行できるようにする関数です。この関数は、対象のページ (「About」) またはそのサブページ (親ページ ID が「2」のページ) を表示している場合に、真を返します。

<!-- 
**Snippet 4**
 -->

**スニペット4**

<!-- 
Add Snippet 4 to your functions.php file, and call is\_tree( ‘id’ ) to see if the current page is the page, or is a sub page of the page. In Snippet 3, is\_tree( ‘2’ ) would replace “is\_page( ‘about’ ) || ‘2’ == $post->post\_parent” inside the first if tag.
 -->

スニペット4をあなたの functions.php ファイルに追加し、`is_tree('id')` をコールし、現在のページがそのページ自体か、そのページのサブページかを確認しましょう。スニペット3では、`is_tree('2')` が、最初の if タグ内の `is_page('about') || '2' == $post->post_parent` を置き換えます。

<!-- 
Note that if you have more than one level of pages the parent page is the one directly above and not the one at the very top of the hierarchy.
 -->

複数の階層を持つページ構造の場合、親ページとは階層構造の最上位にあるページではなく、直上のページを指すことに注意してください。

<!-- 
### Is a Page Template
 -->

### ページ・テンプレート

<!-- 
Allows you to determine whether or not you are in a page template or if a specific page template is being used.
 -->

ページ・テンプレート内にあるかどうか、または特定のページ・テンプレートが使用されているかどうかを判断できます。

<!-- 
[is\_page\_template()](https://developer.wordpress.org/reference/functions/is_page_template/ "Function reference/page template")
 -->

[is\_page\_template()](https://developer.wordpress.org/reference/functions/is_page_template/ "Function reference/page template")

<!-- 
Is a Page Template being used?
 -->

「ページ・テンプレート」が使用されているか否か ?

```php
is_page_template( 'about.php' );
```

<!-- 
Is Page Template ‘about’ being used? Note that unlike other conditionals, if you want to specify a particular Page Template, you need to use the filename, such as about.php or my\_page\_template.php.
 -->

ページ・テンプレート「about」は使用されていますか ? 他の条件分岐とは異なり、特定のページ・テンプレートを指定する場合は、`about.php` や `my_page_template.php` などのファイル名を使用する必要があることに注意してください。

<!-- 
Note: if the file is in a subdirectory you must include this as well. Meaning that this should be the filepath in relation to your theme as well as the filename, for example ‘page-templates/about.php’.
 -->

注: ファイルがサブディレクトリにある場合は、そのパスも必ず含めてください。つまり、これはファイル名だけでなく、テーマ・ディレクトリからの相対パス (たとえば、`page-templates/about.php`) も指定する必要があります。

<!-- 
### A Category Page
 -->

### カテゴリー・ページ

<!-- 
[is\_category()](https://developer.wordpress.org/reference/functions/is_category/ "Function reference/is category")
 -->

[is\_category()](https://developer.wordpress.org/reference/functions/is_category/ "Function reference/is category")

<!-- 
When a Category archive page is being displayed.
 -->

「カテゴリー」アーカイブ・ページが表示されている場合。

```php
is_category( '9' );
```

<!-- 
When the archive page for Category 9 is being displayed.
 -->

「カテゴリー」9の、アーカイブ・ページが表示されている場合。

```php
is_category( 'Stinky Cheeses' );
```

<!-- 
When the archive page for the Category with Name “Stinky Cheeses” is being displayed.
 -->

「臭いチーズ」という名前のカテゴリーの、アーカイブ・ページが表示されている場合。

```php
is_category( 'blue-cheese' );
```

<!-- 
When the archive page for the Category with Category Slug “blue-cheese” is being displayed.
 -->

カテゴリー「blue-cheese」のスラッグを持つカテゴリーの、アーカイブ・ページが表示されている場合。

```php
is_category( array( 9, 'blue-cheese', 'Stinky Cheeses' ) );
```

<!-- 
Returns true when the category of posts being displayed is either term\_ID 9, or slug “blue-cheese”, or name “Stinky Cheeses”.
 -->

表示されている投稿のカテゴリーが、`term_ID` 9、またはスラッグ「blue-cheese」、または名前「臭いチーズ」のいずれかに該当する場合に、真を返します。

```php
in_category( '5' );
```

<!-- 
Returns true if the current post is in the specified category id.
 -->

現在の投稿が、指定されたカテゴリー ID に含まれる場合、真を返します。

```php
in_category( array( 1, 2, 3 ) );
```

<!-- 
Returns true if the current post is in either category 1, 2, or 3.
 -->

現在の投稿が、カテゴリー1、2、または3のいずれかに属する場合、真を返します。

```php
! in_category( array( 4, 5, 6 ) );
```

<!-- 
Returns true if the current post is NOT in either category 4, 5, or 6. Note the ! at the beginning.
 -->

現在の投稿がカテゴリー4、5、または6のいずれにも属していない場合、真を返します。先頭の ! に注意してください。

<!-- 
Note: Be sure to check your spelling when testing. There’s a big difference between “is” or “in”.
 -->

注: テストの際は、必ずスペルを確認してください。「is」と「in」には、大きな違いがあります。

<!-- 
See also [is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function reference/is archive") and [Category Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#category "Template Hierarchy / Category templates").
 -->

[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function reference/is archive") および [カテゴリー・テンプレート](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#category "Template Hierarchy / Category templates") もご覧ください。

<!-- 
### A Tag Page
 -->

### タグ・ページ

<!-- 
[is\_tag()](https://developer.wordpress.org/reference/functions/is_tag/ "Function reference/is tag")
 -->

[is\_tag()](https://developer.wordpress.org/reference/functions/is_tag/ "Function reference/is tag")

<!-- 
When any Tag archive page is being displayed.
 -->

「タグ」アーカイブ・ページが表示されている場合。

```php
is_tag( 'mild' );
```

<!-- 
When the archive page for tag with the slug of ‘mild’ is being displayed.
 -->

タグのスラッグが「mild」であるアーカイブ・ページが表示されている場合。

```php
is_tag( array( 'sharp', 'mild', 'extreme' ) );
```

<!-- 
Returns true when the tag archive being displayed has a slug of either “sharp”, “mild”, or “extreme”.
 -->

表示中のタグ・アーカイブのスラッグが「sharp」、「mild」、または「extreme」のいずれかである場合に、真を返します。

```php
has_tag();
```

<!-- 
When the current post has a tag. Must be used inside The Loop.
 -->

現在の投稿にタグが付いている場合。ループ内で使用する必要があります。

```php
has_tag( 'mild' );
```

<!-- 
When the current post has the tag ‘mild’.
 -->

現在の投稿に「mild」タグが付いている場合。

```php
has_tag( array( 'sharp', 'mild', 'extreme' ) );
```

<!-- 
When the current post has any of the tags in the array.
 -->

現在の投稿が、配列内のいずれかのタグを持っている場合。

<!-- 
See also [is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive") and [Tag Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#tag "Template hierarchy/Tag template").
 -->

[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive") および [タグ・テンプレート](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#tag "Template hierarchy/Tag template") もご覧ください。

<!-- 
### A Taxonomy Page
 -->

### タクソノミー・ページ

<!-- 
[is\_tax()](https://developer.wordpress.org/reference/functions/is_tax/ "Function Reference/is tax")
 -->

[is\_tax()](https://developer.wordpress.org/reference/functions/is_tax/ "Function Reference/is tax")

<!-- 
When any Taxonomy archive page is being displayed.
 -->

任意の「タクソノミー」アーカイブ・ページが表示されている場合。

```php
is_tax( 'flavor' );
```

<!-- 
When a Taxonomy archive page for the flavor taxonomy is being displayed.
 -->

flavor タクソノミーの「タクソノミー」アーカイブ・ページが表示されている場合。

```php
is_tax( 'flavor', 'mild');
```

<!-- 
When the archive page for the flavor taxonomy with the slug of ‘mild’ is being displayed.
 -->

スラッグが「mild」である flavor タクソノミーのアーカイブ・ページが表示されている場合。

```php
is_tax( 'flavor', array( 'sharp', 'mild', 'extreme' ) );
```

<!-- 
Returns true when the flavor taxonomy archive being displayed has a slug of either “sharp”, “mild”, or “extreme”.
 -->

表示されている flavor タクソノミー・アーカイブが「sharp」、「mild」、または「extreme」のスラッグを持つ場合に、真を返します。

<!-- 
[has\_term()](https://developer.wordpress.org/reference/functions/has_term/)
 -->

[has\_term()](https://developer.wordpress.org/reference/functions/has_term/)

<!-- 
Check if the current post has any of given terms. The first parameter should be an empty string. It expects a taxonomy slug/name as a second parameter.
 -->

現在の投稿に、指定されたタームが存在するかどうかをチェックします。最初のパラメータは、空の文字列である必要があります。2番目のパラメータとして、タクソノミーのスラッグ/名前を指定します。

```php
has_term( 'green', 'color' );
```

<!-- 
When the current post has the term ‘green’ from taxonomy ‘color’.
 -->

現在の投稿が、タクソノミー「color」で、「green」というタームを含む場合。

```php
has_term( array( 'green', 'orange', 'blue' ), 'color' );
```

<!-- 
When the current post has any of the terms in the array.
 -->

現在の投稿が、配列内のいずれかのタームを含む場合。

<!-- 
See also [is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive").
 -->

[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive") もご覧ください。

<!-- 
### A Registered Taxonomy
 -->

### 登録済みタクソノミー

<!-- 
[taxonomy\_exists()](https://developer.wordpress.org/reference/functions/taxonomy_exists/ "Function Reference/taxonomy exists")
 -->

[taxonomy\_exists()](https://developer.wordpress.org/reference/functions/taxonomy_exists/ "Function Reference/taxonomy exists")

<!-- 
When a particular taxonomy is registered via [register\_taxonomy()](https://developer.wordpress.org/reference/functions/register_taxonomy/ "Function Reference/Register Taxonomy"). Formerly [is\_taxonomy()](https://developer.wordpress.org/reference/functions/is_taxonomy/) , which was deprecated in Version 3.0
 -->

特定のタクソノミーが [register\_taxonomy()](https://developer.wordpress.org/reference/functions/register_taxonomy/ "Function Reference/Register Taxonomy") によって登録された場合。旧 [is\_taxonomy()](https://developer.wordpress.org/reference/functions/is_taxonomy/) は v3.0で非推奨になりました。

<!-- 
### An Author Page
 -->

### 作者ページ

<!-- 
[is\_author()](https://developer.wordpress.org/reference/functions/is_author/ "Function Reference/is author")
 -->

[is\_author()](https://developer.wordpress.org/reference/functions/is_author/ "Function Reference/is author")

<!-- 
When any Author page is being displayed.
 -->

任意の「作者」ページが表示されている場合。

```php
is_author( '4' );
```

<!-- 
When the archive page for Author number (ID) 4 is being displayed.
 -->

作者番号 (ID) 4のアーカイブ・ページが表示されている場合。

```php
is_author( 'Vivian' );
```

<!-- 
When the archive page for the Author with Nickname “Vivian” is being displayed.
 -->

ニックネーム「Vivian」の「作者」アーカイブ・ページが表示されている場合。

```php
is_author( 'john-jones' );
```

<!-- 
When the archive page for the Author with Nicename “john-jones” is being displayed.
 -->

ニックネーム「john-jones」の「作者」のアーカイブ・ページが表示されている場合。

```php
is_author( array( 4, 'john-jones', 'Vivian' ) );
```

<!-- 
When the archive page for the author is either user ID 4, or user\_nicename “john-jones”, or nickname “Vivian”.
 -->

作者のアーカイブ・ページが、ユーザー ID4、または `user_nicename`「john-jones」、またはニックネーム「Vivian」のいずれかである場合。

<!-- 
See also [is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive") and [Author Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#author-display).
 -->

[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive") および [作者テンプレート](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#author-display) もご覧ください。

<!-- 
### A Multi-author Site
 -->

### 複数投稿者サイト

<!-- 
[is\_multi\_author()](https://developer.wordpress.org/reference/functions/is_multi_author/ "Function Reference/is multi author")
 -->

[is\_multi\_author()](https://developer.wordpress.org/reference/functions/is_multi_author/ "Function Reference/is multi author")

<!-- 
When more than one author has published posts for a site. Available with Version 3.2.
 -->

複数の投稿者がサイトに投稿を公開した場合。v3.2で利用できるようになりました。

<!-- 
### A Date Page
 -->

### 日付ページ

<!-- 
[is\_date()](https://developer.wordpress.org/reference/functions/is_date/ "Function Reference/is date")
 -->

[is\_date()](https://developer.wordpress.org/reference/functions/is_date/ "Function Reference/is date")

<!-- 
When any date-based archive page is being displayed (i.e. a monthly, yearly, daily or time-based archive).
 -->

任意の日付ベースのアーカイブ・ページが表示されている場合 (たとえば、月別、年別、日別、または時間ベースのアーカイブ)。

<!-- 
[is\_year()](https://developer.wordpress.org/reference/functions/is_year/ "Function Reference/is year")
 -->

[is\_year()](https://developer.wordpress.org/reference/functions/is_year/ "Function Reference/is year")

<!-- 
When a yearly archive is being displayed.
 -->

年別アーカイブが表示されている場合。

<!-- 
[is\_month()](https://developer.wordpress.org/reference/functions/is_month/ "Function Reference/is month")
 -->

[is\_month()](https://developer.wordpress.org/reference/functions/is_month/ "Function Reference/is month")

<!-- 
When a monthly archive is being displayed.
 -->

月別アーカイブが表示されている場合。

<!-- 
[is\_day()](https://developer.wordpress.org/reference/functions/is_day/ "Function Reference/is day")
 -->

[is\_day()](https://developer.wordpress.org/reference/functions/is_day/ "Function Reference/is day")

<!-- 
When a daily archive is being displayed.
 -->

日別アーカイブが表示されている場合。

<!-- 
[is\_time()](https://developer.wordpress.org/reference/functions/is_time/ "Function Reference/is time")
 -->

[is\_time()](https://developer.wordpress.org/reference/functions/is_time/ "Function Reference/is time")

<!-- 
When an hourly, “minutely”, or “secondly” archive is being displayed.
 -->

時間単位、分単位、または秒単位のアーカイブが表示されている場合。

<!-- 
[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/ "Function Reference/is new day")
 -->

[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/ "Function Reference/is new day")

<!-- 
If today is a new day according to post date. Should be used inside the loop.
 -->

投稿日時にもとづいて、今日が新しい日である場合。ループ内で使用すべきです。

<!-- 
### Any Archive Page
 -->

### 任意のアーカイブ・ページ

<!-- 
[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")
 -->

[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")

<!-- 
When any type of Archive page is being displayed. Category, Tag, Author and Date based pages are all types of Archives.
 -->

任意のタイプのアーカイブ・ページが表示されている場合。カテゴリー、タグ、投稿者、日付にもとづくページは、すべてアーカイブのタイプです。

<!-- 
### A Search Result Page
 -->

### 検索結果ページ

<!-- 
[is\_search()](https://developer.wordpress.org/reference/functions/is_search/ "Function Reference/is search")
 -->

[is\_search()](https://developer.wordpress.org/reference/functions/is_search/ "Function Reference/is search")

<!-- 
When a search result page archive is being displayed.
 -->

検索結果ページのアーカイブが表示されている場合。

<!-- 
### A 404 Not Found Page
 -->

### `404` Not Found ページ

<!-- 
[is\_404()](https://developer.wordpress.org/reference/functions/is_404/ "Function Reference/is 404")
 -->

[is\_404()](https://developer.wordpress.org/reference/functions/is_404/ "Function Reference/is 404")

<!-- 
When a page displays after an “HTTP 404: Not Found” error occurs.
 -->

`HTTP 404: Not Found` エラーが発生した後にページが表示される場合。

<!-- 
### A Privacy Policy Page
 -->

### 個人情報の保護方針ページ

<!-- 
[is\_privacy\_policy()](https://developer.wordpress.org/reference/functions/is_privacy_policy/)
 -->

[is\_privacy\_policy()](https://developer.wordpress.org/reference/functions/is_privacy_policy/)

<!-- 
When the Privacy Policy page is being displayed.
 -->

「個人情報の保護方針」ページが表示されている場合。

<!-- 
### An Attachment
 -->

### 添付ファイル

<!-- 
[is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment/ "Function Reference/is attachment")
 -->

[is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment/ "Function Reference/is attachment")

<!-- 
When an attachment document to a post or Page is being displayed. An attachment is an image or other file uploaded through the post editor’s upload utility. Attachments can be displayed on their own ‘page’ or template.
 -->

投稿や「ページ」への添付ファイルが表示されている場合。添付ファイルとは、投稿エディターのアップロード機能を通じてアップロードされた画像やその他のファイルを指します。添付ファイルは、専用の「ページ」またはテンプレート上で表示できます。

<!-- 
### A Single Page, Single Post or Attachment
 -->

### 個別ページ、個別投稿、または添付ファイル

<!-- 
[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/ "Function Reference/is singular")
 -->

[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/ "Function Reference/is singular")

<!-- 
When any of the following return true: `is_single()`, `is_page()` or `is_attachment()`.
 -->

以下のいずれかが真を返す場合: `is_single()`、`is_page()` または `is_attachment()`。

```php
is_singular( 'book' );
```

<!-- 
True when viewing a post of the Custom Post Types book.
 -->

カスタム投稿タイプ book の投稿を表示している場合、真。

```php
is_singular( array( 'newspaper', 'book' ) );
```

<!-- 
True when viewing a post of the Custom Post Types newspaper or book.
 -->

カスタム投稿タイプ newspaper または book の投稿を表示している場合、真。

<!-- 
### A Syndication
 -->

### 配信

<!-- 
[is\_feed()](https://developer.wordpress.org/reference/functions/is_feed/ "Function Reference/is feed")
 -->

[is\_feed()](https://developer.wordpress.org/reference/functions/is_feed/ "Function Reference/is feed")

<!-- 
When the site requested is a Syndication. This tag is not typically used by users; it is used internally by WordPress and is available for Plugin Developers.
 -->

サイトがリクエストしたものが、配信である場合。このタグは通常ユーザーによって使用されるものでは、ありません; WordPress によって内部的に使用され、プラグイン開発者が利用可能です。

<!-- 
### A Trackback
 -->

### トラックバック

<!-- 
[is\_trackback()](https://developer.wordpress.org/reference/functions/is_trackback/ "Function Reference/is trackback")
 -->

[is\_trackback()](https://developer.wordpress.org/reference/functions/is_trackback/ "Function Reference/is trackback")

<!-- 
When the site requested is WordPress’ hook into its Trackback engine. This tag is not typically used by users; it is used internally by WordPress and is available for Plugin Developers.
 -->

サイトがリクエストしたものが、WordPress のトラックバック・エンジンへのフックである場合。このタグは通常、ユーザーによって使用されるものではありません; WordPress によって内部的に使用され、プラグイン開発者が利用可能です。

<!-- 
### A Preview
 -->

### プレビュー

<!-- 
[is\_preview()](https://developer.wordpress.org/reference/functions/is_preview/ "Function Reference/is preview")
 -->

[is\_preview()](https://developer.wordpress.org/reference/functions/is_preview/ "Function Reference/is preview")

<!-- 
When a single post being displayed is viewed in Draft mode.
 -->

表示中の個別投稿が、下書きモードで表示されている場合。

<!-- 
### Has An Excerpt
 -->

### 抜粋あり

<!-- 
[has\_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/ "Function Reference/has excerpt")
 -->

[has\_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/ "Function Reference/has excerpt")

<!-- 
When the current post has an excerpt
 -->

現在の投稿に抜粋がある場合。

<!-- 
**has\_excerpt( 42 )**
 -->

**`has_excerpt( 42 )`**

<!-- 
When the post 42 (ID) has an excerpt.
 -->

投稿42 (ID) に抜粋がある場合。

```php
<?php
// Get $post if you're inside a function global $post;
if ( empty( $post->post_excerpt ) ) {
	// This post has no excerpt
} else {
	// This post has excerpt
}
```

<!-- 
**Other use**  
 -->

**その他の用途**  

<!-- 
When you need to hide the auto displayed excerpt and only display your post’s excerpts.
 -->

自動表示される抜粋を非表示にし、あなたの投稿の抜粋のみを表示する必要がある場合。

```php
<?php
if ( ! has_excerpt() ) {
	echo '';
} else {
	the_excerpt();
}
```

<!-- 
Replace auto excerpt for a text or code.
 -->

テキストまたはコードの自動抜粋を置換します。

```php
<?php if ( ! has_excerpt() ) {
	// your text or code
}
```

<!-- 
### Has A Nav Menu Assigned
 -->

### ナビゲーション・メニュー割り当て済み

<!-- 
[has\_nav\_menu()](https://developer.wordpress.org/reference/functions/has_nav_menu/ "Function Reference/has nav menu")
 -->

[has\_nav\_menu()](https://developer.wordpress.org/reference/functions/has_nav_menu/ "Function Reference/has nav menu")

<!-- 
Whether a registered nav menu location has a menu assigned
 -->

登録済みナビゲーション・メニューのロケーションに、メニューが割り当てられているかどうか

<!-- 
Returns: assigned(true) or not(false)
 -->

戻り値: 割り当て済み (真) または、未割り当て (偽)

<!-- 
### Inside The Loop
 -->

### ループ内

<!-- 
[in\_the\_loop()](https://developer.wordpress.org/reference/functions/in_the_loop/ "Function Refence/in the loop")
 -->

[in\_the\_loop()](https://developer.wordpress.org/reference/functions/in_the_loop/ "Function Refence/in the loop")

<!-- 
Check to see if you are “inside the loop”. Useful for plugin authors, this conditional returns as true when you are inside the loop.
 -->

あなたが「ループ内」にいるかどうかを、チェックします。プラグイン作者に有用なこの条件式は、あなたがループ内にいる場合に、真を返します。

<!-- 
### Is Sidebar Active
 -->

### サイドバーが有効

<!-- 
[is\_active\_sidebar()](https://developer.wordpress.org/reference/functions/is_active_sidebar/ "Function Reference/is active sidebar")
 -->

[is\_active\_sidebar()](https://developer.wordpress.org/reference/functions/is_active_sidebar/ "Function Reference/is active sidebar")

<!-- 
Check to see if a given sidebar is active (in use). Returns true if the sidebar (identified by name, id, or number) is in use, otherwise the function returns false.
 -->

指定されたサイドバーがアクティブ (使用中) かどうかをチェックします。(名前、ID、または番号で識別される) サイドバーが使用中の場合、関数は真を返します。それ以外の場合は、偽を返します。

<!-- 
### Part of a Network (Multisite)
 -->

### ネットワークの一部 (マルチ・サイト)

<!-- 
[is\_multisite()](https://developer.wordpress.org/reference/functions/is_multisite/ "Function Reference/is multisite")
 -->

[is\_multisite()](https://developer.wordpress.org/reference/functions/is_multisite/ "Function Reference/is multisite")

<!-- 
Check to see whether the current site is in a WordPress MultiSite install.
 -->

現在のサイトが WordPress マルチサイト・インストール環境にあるかどうかをチェックします。

<!-- 
### Main Site (Multisite)
 -->

### メイン・サイト (マルチ・サイト)

<!-- 
[is\_main\_site()](https://developer.wordpress.org/reference/functions/is_main_site/ "Function Reference/is main site")
 -->

[is\_main\_site()](https://developer.wordpress.org/reference/functions/is_main_site/ "Function Reference/is main site")

<!-- 
Determines if a site is the main site in a network.
 -->

サイトがネットワーク内のメインサイトであるかどうかを判定します。

<!-- 
### Admin of a Network (Multisite)
 -->

### ネットワーク管理者 (マルチ・サイト)

<!-- 
[is\_super\_admin()](https://developer.wordpress.org/reference/functions/is_super_admin/ "Function Reference/is super admin")
 -->

[is\_super\_admin()](https://developer.wordpress.org/reference/functions/is_super_admin/ "Function Reference/is super admin")

<!-- 
Determines if a user is a network (super) admin.
 -->

ユーザーがネットワーク (特権) 管理者であるかどうかを判定します。

<!-- 
### An Active Plugin
 -->

### 有効化済みプラグイン

<!-- 
[is\_plugin\_active()](https://developer.wordpress.org/reference/functions/is_plugin_active/ "Function Reference/is plugin active")
 -->

[is\_plugin\_active()](https://developer.wordpress.org/reference/functions/is_plugin_active/ "Function Reference/is plugin active")

<!-- 
Checks if a plugin is activated.
 -->

プラグインが有効化されているかどうかを確認します。

<!-- 
### A Child Theme
 -->

### 子テーマ

<!-- 
[is\_child\_theme()](https://developer.wordpress.org/reference/functions/is_child_theme/ "Function Reference/is child theme")
 -->

[is\_child\_theme()](https://developer.wordpress.org/reference/functions/is_child_theme/ "Function Reference/is child theme")

<!-- 
Checks whether a child theme is in use.
 -->

子テーマが使用されているかどうかを確認します。

<!-- 
### Theme supports a feature
 -->

### テーマ対応機能

<!-- 
[current\_theme\_supports()](https://developer.wordpress.org/reference/functions/current_theme_supports/ "Function Reference/current theme supports")
 -->

[current\_theme\_supports()](https://developer.wordpress.org/reference/functions/current_theme_supports/ "Function Reference/current theme supports")

<!-- 
Checks if various theme features exist.
 -->

さまざまなテーマ機能が存在するかどうかを確認します。

<!-- 
## Working Examples
 -->

## 動作例

<!-- 
Here are working samples to demonstrate how to use these conditional tags.
 -->

以下に、これらの条件付きタグの使用方法を示す、動作サンプルを示します。

<!-- 
### Single Post
 -->

### 個別投稿

<!-- 
This example shows how to use `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` to display something specific only when viewing a single post page:
 -->

この例は、個別投稿ページを表示している場合にのみ、特定のものを表示するために `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` を使用する方法を示しています:

```php
<?php
if ( is_single() ) {
	echo 'This is just one of many fabulous entries in the ' . single_cat_title() . ' category!';
}
```

<!-- 
Another example of how to use Conditional Tags in the Loop. Choose to display content or excerpt in index.php when this is a display single post or the home page.
 -->

ループ内での「条件付きタグ」の、別の使用例です。index.php で、個別投稿の表示時またはホームページでの表示時に、コンテンツ全体または抜粋を表示するかを選択します。

```php
<?php
if ( is_home() || is_single() ) {
	the_content();
} else {
	the_excerpt();
}
```

<!-- 
When you need display a code or element, in a place that is NOT the home page.
 -->

ホームページ以外の場所で、コードや要素を表示する必要がある場合。

```php
<?php if ( ! is_home() ) {
	// Insert your markup ...
}
```

<!-- 
### Check for Multiple Conditionals
 -->

### 複数条件の確認

<!-- 
You can use [PHP operators](https://www.php.net/manual/en/language.operators.php) to evaluate multiple conditionals in a single if statement.
 -->

[PHP 演算子](https://www.php.net/manual/en/language.operators.php) を使用すると、単一の if 文内で複数の条件式を評価できます。

<!-- 
This is handy if you need to check whether combinations of conditionals evaluate to true or false.
 -->

条件式の組み合わせが真か偽かを評価する必要がある場合に、便利です。

```php
<?php

// Check to see if any of 2 conditionals are met.
if ( is_single() || is_page() ) {
	// If it's a single post or a single page, do something special.
}
if ( is_archive() && ! is_category( 'nachos' ) ) {
	// If it's an archive page for any category EXCEPT nachos, do something special.
}
```

```php
<?php

// Check to see if 3 conditionals are met.
if ( $query->is_main_query() && is_post_type_archive( 'products' ) && ! is_admin() ) {
	// If it's the main query on a custom post type archive for Products.
	// And if we're not in the WordPress admin, then do something special.
}

if ( is_post_type_archive( 'movies' ) || is_tax( 'genre' ) || is_tax( 'actor' ) ) {
	// If it's a custom post type archive for Movies.
	// Or it's a taxonomy archive for Genre.
	// Or it's a taxonomy archive for Actor, do something special.
}
```

<!-- 
### Date Based Differences
 -->

### 日付にもとづく変更

<!-- 
If someone browses our site by date, let’s distinguish posts in different years by using different colors:
 -->

もし誰かが本サイトを日付別に閲覧する場合、異なる年の投稿を色分けして区別しましょう:

```php
<?php if ( have_posts() ) : while ( have_posts() ) : the_post(); ?>

	<h2 id="post-<?php the_ID(); ?>">
		<a href="<?php the_permalink(); ?>" rel="bookmark"><?php the_title(); ?></a>
	</h2>

	<small>
		<?php the_time( 'F jS, Y' ); ?> by <?php the_author(); ?>
	</small>

	<?php
	// Are we showing a date-based archive?
	if ( is_date() ) {
		if ( date( 'Y' ) != get_the_date( 'Y' ) ) {
			// this post was written in a previous year
			// so let's style the content using the "oldentry" class
			echo '<div class="oldentry">';
		} else {
			echo '<div class="entry">';
		}
	} else {
		echo '<div class="entry">';
	}
	the_content( 'Read the rest of this entry »' );
	echo '</div>';
	?>

<?php endwhile; endif; ?>
```

<!-- 
### Variable Sidebar Content
 -->

### 可変サイドバー・コンテンツ

<!-- 
This example will display different content in your sidebar based on what page the reader is currently viewing.
 -->

本例では、読者が現在閲覧しているページにもとづいて、あなたのサイドバーに異なるコンテンツを表示します。

```php
<div id="sidebar">

<?php
// Let's generate info appropriate to the page being displayed.
if ( is_home() ) {
	// We're on the home page, so let's show a list of all top-level categories.
	wp_list_categories( 'optionall=0&sort_column=name&list=1&children=0' );
} elseif ( is_category() ) {
	// We're looking at a single category view, so let's show _all_ the categories.
	wp_list_categories( 'optionall=1&sort_column=name&list=1&children=1&hierarchical=1' );
} elseif ( is_single() ) {
	// We're looking at a single page, so let's not show anything in the sidebar.
} elseif ( is_page() ) {
	// We're looking at a static page. Which one?
	if ( is_page( 'About' ) ) {
		// Our about page.
		echo 'This is my about page!';
	} elseif ( is_page( 'Colophon' ) ) {
		echo 'This is my colophon page, running on WordPress ' . bloginfo( 'version' ) . '';
	} else {
		// Catch-all for other pages.
		echo 'Vote for Pedro!';
	}
} else {
	// Catch-all for everything else (archives, searches, 404s, etc)
	echo 'Pedro offers you his protection.';
}
?>

</div><!-- #sidebar -->
```

<!-- 
### Helpful 404 Page
 -->

### 便利な404ページ

<!-- 
The [Creating an Error 404 Page](https://codex.wordpress.org/Creating_an_Error_404_Page) article as an example of using the PHP conditional function `isset()` in the [Writing Friendly Messages](https://codex.wordpress.org/Creating_an_Error_404_Page#Writing_Friendly_Messages) section.
 -->

[404エラーページの作成](https://codex.wordpress.org/Creating_an_Error_404_Page) 記事は、[フレンドリーなメッセージの記述](https://codex.wordpress.org/Creating_an_Error_404_Page#Writing_Friendly_Messages) セクションにおける、PHP の条件関数 `isset()` の使用例として挙げられています。

<!-- 
### In the theme’s footer.php file
 -->

### テーマの `footer.php` ファイル内

<!-- 
At times queries performed in other templates such as sidebar.php may corrupt certain conditional tags. For instance, in header.php a conditional tag works properly but doesn’t work in a theme’s footer.php. The trick is to put wp\_reset\_query before the conditional test in the footer. For example:
 -->

sidebar.php などの他のテンプレートで実行されたクエリーが、特定の条件付きタグを破損させる場合があります。たとえば、header.php では正常に動作する条件付きタグが、テーマの footer.php では動作しないことがあります。解決策は、footer 内の条件判定の前に `wp_reset_query` を挿入することです。たとえば:

```php
<?php
wp_reset_query();
if ( is_page( '2' ) ) {
	echo 'This is page 2!';
}
```

<!-- 
## Conditional Tags Index
 -->

## 条件タグ索引

<!-- 
> [List of Conditional Tags](https://developer.wordpress.org/themes/references/list-of-conditional-tags/)
 -->

> [条件付きタグの一覧](https://developer.wordpress.org/themes/references/list-of-conditional-tags/)

<!-- 
## Function Reference
 -->

## 関数リファレンス

<!-- 
[Reference](https://developer.wordpress.org/?s=is_)
 -->

[リファレンス](https://developer.wordpress.org/?s=is_)