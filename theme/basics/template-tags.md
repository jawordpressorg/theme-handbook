<!--
# Template Tags
 -->

# テンプレート・タグ

<!--
Template tags are used within themes to **retrieve content from your database**. The content could be anything from a blog title to a complete sidebar. Template tags are the preferred method to pull content into your theme because:
 -->

テンプレート・タグは、テーマ内で **あなたのデータベースから、コンテンツを取得する** ために使用されます。コンテンツは、ブログのタイトルから完全なサイドバーまで、あらゆるものになり得ます。テンプレート・タグは、コンテンツをあなたのテーマに取り込むための推奨される方法です。その理由は:

<!--
*   they can print dynamic content;
*   they can be used in multiple theme files; and
*   they separate the theme into smaller, more understandable, sections.
 -->

*   動的コンテンツを出力できます;
*   複数のテーマファイルで使用できます; そして
*   テーマを、より小さく、より理解しやすい、セクションに分割します。

<!--
## What is a Template Tag?
 -->

## テンプレート・タグって ?

<!--
A template tag is simply a piece of code that tells WordPress to get something from the database. It is broken up into three components:
 -->

テンプレート・タグとは、WordPress にデータベースから何かを取得するよう指示する、コードの断片です。これは3つのコンポーネントに分けられます:

<!--
*   A PHP code tag
*   A WordPress function
*   Optional parameters
 -->

*   PHP コード・タグ
*   WordPress 関数
*   任意のパラメータ

<!--
You can use a template tag to call another theme file or some information from the database.
 -->

テンプレート・タグを使用して、別のテーマ・ファイルやデータベースからの情報をコールできます。

<!--
For example, the template tag `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` tells WordPress to get the `header.php` file and include it in the current theme file. Similarly, `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` tells WordPress to get the footer.php file.
 -->

たとえば、テンプレート・タグ `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` は WordPress に `header.php` ファイルを取得し、現在のテーマ・ファイルにインクルードするよう指示します。同様に、`[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` は WordPress に `footer.php` ファイルを取得するよう指示します。

<!--
There are also other kinds of template tags:
 -->

他にも、次のような種類のテンプレート・タグがあります:

<!--
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – tells WordPress to get the title of the page or post from the database and include it.
*   `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` – tells WordPress to get the blog title out of the database and include it in the template file.
 -->

*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – WordPress に、データベースからページまたは投稿のタイトルを取得して、インクルードするよう指示します。
*   `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` – WordPress に、データベースからブログ・タイトルを取得して、テンプレート・ファイルにインクルードするよう指示します。

<!--
If you look closely at the last example, you will also see that there is a parameter between the parenthesis. Parameters let you do two things:
 -->

最後の例をよく見ると、括弧の間にパラメータがあることもわかります。パラメータを使うと、次の2つのことが可能になります:

<!--
1.  ask for specific pieces of information and
2.  format the information in a certain way.
 -->

1.  情報の特定の部分を要求でき、そして
2.  特定の方法で、その情報をフォーマットできます。

<!--
[Parameters are covered extensively below](#parameters), but it’s useful to be aware that you can send WordPress-specific instructions for how you want the data presented.
 -->

[パラメータについては、以下で詳しく説明します](#parameters) が、データの提示方法について、WordPress 固有の指示を送れることを認識しておくことは有用です。

<!--
## Why Use Template Tags
 -->

## テンプレート・タグを使用する理由

<!--
By encapsulating all of the code for a particular chunk of content, template tags make it very easy to include various pieces of a template in a theme file and also to maintain the theme.
 -->

コンテンツの特定の部分に関するコードをすべてカプセル化することで、テンプレート・タグを使用すると、テーマ・ファイル内でテンプレートのさまざまな部分を簡単にインクルードでき、テーマのメンテナンスも容易になります。

<!--
It is far easier to create one `header.php` file and have all of your theme templates like `single.php`, `page.php`, `front-page.php`, etc. reference that one theme file using `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` than copying and pasting the code into each theme file. It also makes maintenance easier. Whenever you make a change in your `header.php` file, the change is automatically carried over into all of your other theme files.
 -->

各テーマ・ファイルにコードをコピー & ペーストするよりも、`header.php` ファイルを1つ作成し、`single.php`、`page.php`、`front-page.php` などのあなたのテーマ・テンプレートすべてが `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` を使用して、その1つのテーマ・ファイルを参照するようにするほうがはるかに簡単です。また、メンテナンスも容易になります。あなたの `header.php` ファイルで変更を加えるたびに、その変更は自動的に、あなたの他のすべてテーマ・ファイルに反映されます。

<!--
Another reason to use template tags is to display dynamic data, i.e. data from the database. In your header, you could manually include the `title` tag, like so:
 -->

テンプレート・タグを使用するもう一つの理由は、動的データ (たとえばデータベースからのデータ) を表示するためです。あなたのヘッダーでは、以下のように手動で `title` タグをインクルードできます:

```xml
<title>My Personal Website</title>
```

<!--
However, doing this means manually editing your theme any time you want to change the title of your website. Instead, it’s easier to include the `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` template tag, which automatically fetch the site title from the database. Now, you can change the title of your site in WordPress, rather than having to hard code your theme templates.
 -->

しかしながら、こうすると、あなたの Web サイトのタイトルを変更するたびに、あなたのテーマを手動で編集する必要があります。代わりに、データベースからサイトタイトルを自動的に取得する `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` テンプレート・タグを使用するほうが簡単です。これで、あなたのテーマ・テンプレートをハードコードする必要なく、WordPress であなたのサイトのタイトルを変更できます。

<!--
## How to Use Template Tags
 -->

## テンプレート・タグの使い方

<!--
Using template tags is very simple. In any template file you can use a template tag by simply printing one line of php code to call the template tag. Printing the header.php file is as simple as:
 -->

テンプレート・タグの使用は、非常に簡単です。どのテンプレート・ファイルでも、たった一行の PHP コードを記述するだけで、テンプレート・タグをコールできます。`header.php` ファイルを出力するのは、以下のように簡単です:

```php
get_header();
```

<!--
### Parameters
 -->

### パラメータ

<!--
Some template tags let you pass parameters. Parameters are extra pieces of information that determine what is retrieved from the database.
 -->

一部のテンプレート・タグでは、パラメータを渡すことができます。パラメータとは、データベースから何を取り出すかを決定する、追加の情報です。

<!--
For example, the `[bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/ "bloginfo template tag")` template tag allows you to give it a parameter telling WordPress the specific piece of information you want. To print the blog name, you just pass along the parameter “name,” like so:
 -->

たとえば、`[bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/ "bloginfo template tag")` テンプレート・タグでは、取得したい特定の情報を指定するパラメータを、WordPress に伝えることができます。ブログ名を出力するには、次のように「name」パラメータを渡すだけです:

```php
bloginfo( 'name' );
```

<!--
To print the version of WordPress that the blog is running on, you would pass a parameter of “version”:
 -->

ブログが稼働している WordPress のバージョンを出力するには、「version」というパラメータを渡します:

```php
bloginfo( 'version' );
```

<!--
For each template tag, the parameters differ. A list of the parameters and what they can do can be found on specific template tag pages located throughout the [code reference](https://developer.wordpress.org/reference/).
 -->

各テンプレート・タグで、パラメータは異なります。パラメータの一覧とその機能は、[コード・リファレンス](https://developer.wordpress.org/reference/)内の、特定のテンプレート・タグ・ページで確認できます。

<!--
### Using Template Tags Within the Loop
 -->

### ループ内での、テンプレート・タグの使用

<!--
Many template tags work within the [WordPress Loop](https://developer.wordpress.org/themes/basics/the-loop/). This means that they are included in the template files as part of the php “loop” that generates the pages users see based upon the instructions inside of the loop.
 -->

多くのテンプレート・タグは、[WordPress ループ](https://developer.wordpress.org/themes/basics/the-loop/) 内で動作します。これは、テンプレート・ファイル内でページを生成する PHP の「ループ」の一部としてインクルードされており、ループ内の指示にもとづいて表示されるページを、ユーザーは閲覧することを意味します。

<!--
The WordPress loop begins with:
 -->

WordPress のループは、以下のように始まります:

```php
if ( have_posts() ) :
	while ( have_posts() ) :
		the_post();
```

<!--
Template tags that work within the loop must be in the middle area, before the ending section of the loop below:
 -->

ループ内で動作するテンプレート・タグは、以下のループ終了セクションの前にある、中間領域に配置する必要があります:

```php
	endwhile;
else :
	_e( 'Sorry, no posts matched your criteria.', 'devhub' );
endif;
```

<!--
Some of template tags that need to be inside of the loop include
 -->

ループ内に配置する必要があるテンプレート・タグには、以下が含まれます

<!-- 
*   [the\_content()](https://developer.wordpress.org/reference/functions/the_content/)
*   [the\_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)
*   [next\_post()](https://developer.wordpress.org/reference/functions/next_post/)
*   [previous\_post()](https://developer.wordpress.org/reference/functions/previous_post/)
 -->

*   [`the_content()`](https://developer.wordpress.org/reference/functions/the_content/)
*   [`the_excerpt()`](https://developer.wordpress.org/reference/functions/the_excerpt/)
*   [`next_post()`](https://developer.wordpress.org/reference/functions/next_post/)
*   [`previous_post()`](https://developer.wordpress.org/reference/functions/previous_post/)

<!--
The main reason why some functions require the loop is because they require the global post object to be set.
 -->

いくつかの関数がループを必要とする主な理由は、グローバル投稿オブジェクトが、セットされている必要があるためです。

<!--
If the template tag you want to use doesn’t have to be within the loop
 -->

使用したいテンプレート・タグが、ループ内に配置する必要がない場合

<!-- 
*   [wp\_list\_cats()](https://developer.wordpress.org/reference/functions/wp_list_cats/)
*   [wp\_list\_pages()](https://developer.wordpress.org/reference/functions/wp_list_pages/)
 -->

*   [`wp_list_cats()`](https://developer.wordpress.org/reference/functions/wp_list_cats/)
*   [`wp_list_pages()`](https://developer.wordpress.org/reference/functions/wp_list_pages/)

<!--
then you can put it in any file you’d like, for instance in the sidebar, header, or footer template files.
 -->

その後、たとえばサイドバー、ヘッダー、フッターのテンプレート・ファイルなど、任意のファイルに配置できます。

<!--
These are functions that typically do not require the global post object.
 -->

これらは通常、グローバル投稿オブジェクトを必要としない関数です。

<!--
## See Also
 -->
## 関連項目

<!--
*   [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/)
*   [Complete list of Template Tags](https://developer.wordpress.org/themes/references/list-of-template-tags/)
*   [Plugin API Hooks](_wp_link_placeholder)
 -->

*   [条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/)
*   [テンプレート・タグの完全リスト](https://developer.wordpress.org/themes/references/list-of-template-tags/)
*   [プラグイン API フック](_wp_link_placeholder)