<!--
# Template Tags
-->
# テンプレートタグ

<!--
Template tags are used within themes to **retrieve content from your database**. The content could be anything from a blog title to a complete sidebar. Template tags are the preferred method to pull content into your theme because:
-->
テンプレートタグは、テーマの中でブログのタイトルや完全なサイドバーといった**コンテンツをデータベースから取得する**際に使用します。次の理由から、テーマでコンテンツを表示する方法としてテンプレートタグが推奨されます:

<!--
*   they can print dynamic content;
*   they can be used in multiple theme files; and
*   they separate the theme into smaller, more understandable, sections.
-->
*   コンテンツを動的に表示できます
*   複数のテーマファイルの中で使用できます
*   テーマファイルを小さく、わかりやすい単位に分けられます

<!--
## What is a Template Tag?
-->
## テンプレートタグとは ?

<!--
A template tag is simply a piece of code that tells WordPress to get something from the database. It is broken up into three components:
-->
テンプレートタグは、データベースから何かを取得するときに使う簡単なコードです。次の3つの要素で構成されています:

<!--
*   A PHP code tag
*   A WordPress function
*   Optional parameters
-->
*   PHP コードタグ
*   WordPress 関数
*   任意のパラメータ

<!--
You can use a template tag to call another theme file or some information from the database.
-->
テンプレートタグを使って、他のテーマファイルやデータベースの情報を取得できます。

<!--
For example, the template tag `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` tells WordPress to get the `header.php` file and include it in the current theme file. Similarly, `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` tells WordPress to get the footer.php file.
-->
たとえば `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` を使うと `header.php` ファイルを取得して、その内容を現在のテーマファイルの中に含めることができます。同様に、 `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` を使うと `footer.php` の内容を取得できます。

<!--
There are also other kinds of template tags:
-->
その他にもさまざまな種類のテンプレートタグがあります:

<!--
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – tells WordPress to get the title of the page or post from the database and include it.
*   `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` – tells WordPress to get the blog title out of the database and include it in the template file.
-->
*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – データベースからページのタイトルを取得して、テンプレートファイルに含めます。
*   `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` – データベースからブログのタイトルを取得して、テンプレートファイルに含めます。

<!--
If you look closely at the last example, you will also see that there is a parameter between the parenthesis. Parameters let you do two things:
-->
上記の例には、括弧の中にパラメータが含まれていることがわかります。パラメータを使うと次の2つのことができます:

<!--
1.  ask for specific pieces of information and
2.  format the information in a certain way.
-->
1.  特定の情報を取得する
2.  情報を任意の方法でフォーマットする

<!--
[Parameters are covered extensively below](#parameters), but it’s useful to be aware that you can send WordPress-specific instructions for how you want the data presented.
-->
[パラメーターについては以下で詳しく説明します](#parameters)が、 WordPress 固有のタグでデータの表示方法を制御できることを知っておくと便利です。

<!--
## Why Use Template Tags
-->
## なぜテンプレートタグを使うのか

<!--
By encapsulating all of the code for a particular chunk of content, template tags make it very easy to include various pieces of a template in a theme file and also to maintain the theme.
-->
テンプレートタグを使うとコンテンツの任意の部分をカプセル化できるので、テーマファイルにさまざまな種類のテンプレートを含めることが簡単になり、テーマの保守も容易になります。

<!--
It is far easier to create one `header.php` file and have all of your theme templates like `single.php`, `page.php`, `front-page.php`, etc. reference that one theme file using `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` than copying and pasting the code into each theme file. It also makes maintenance easier. Whenever you make a change in your `header.php` file, the change is automatically carried over into all of your other theme files.
-->
`header.php` ファイルを1つ作成して `single.php`, `page.php`, `front-page.php` といったテーマファイルで `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` を使ってその内容を参照するほうが、各テーマファイルの中にまったく同じコードをコピー&ペーストするよりもはるかに簡単です。 `header.php` ファイルを編集すると、自動的にすべてのテーマファイルの中に反映されるので、テーマの保守も容易になります。

<!--
Another reason to use template tags is to display dynamic data, i.e. data from the database. In your header, you could manually include the `title` tag, like so:
-->
また、テンプレートタグを使うことで、データベースから取得するような動的なデータの表示も可能です。ヘッダーの中に `title` タグを含める際、次のようにハードコードできます:

```xml
<title>My Personal Website</title>
```

<!--
However, doing this means manually editing your theme any time you want to change the title of your website. Instead, it’s easier to include the `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` template tag, which automatically fetch the site title from the database. Now, you can change the title of your site in WordPress, rather than having to hard code your theme templates.
-->
しかし、このようにハードコードしてしまうと、 Web サイトのタイトルを変更したい場合に毎回テーマを書き換える必要があります。その代わりに、テンプレートタグ `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` を使うとデータベースから自動的にサイトのタイトルが取得できるので、 Web サイトのタイトルを変更したい場合は WordPress の管理画面上で変更するだけで済みます。

<!--
## How to Use Template Tags
-->
## テンプレートタグの使い方

<!--
Using template tags is very simple. In any template file you can use a template tag by simply printing one line of php code to call the template tag. Printing the header.php file is as simple as:
-->
テンプレートタグの使い方は簡単です。テンプレートファイルの中で php のコードを1行含めるだけでテンプレートタグが使えます。たとえば `header.php` の内容を表示したいときは次のように書くだけです:

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
テンプレートタグの中にはパラメータを指定できるものがあります。パラメータを使うと、データベースから取得する情報を細かく指定できます。

<!--
For example, the `[bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/ "bloginfo template tag")` template tag allows you to give it a parameter telling WordPress the specific piece of information you want. To print the blog name, you just pass along the parameter “name,” like so:
-->
たとえば、 `[bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/)` テンプレートタグでは WordPress に関する情報のうち、どの情報を取得するかをパラメータで指定できます。ブログの名前を表示するには、パラメータとして "name" を指定します:

```php
bloginfo( 'name' );
```

<!--
To print the version of WordPress that the blog is running on, you would pass a parameter of “version”:
-->
ブログに使用している WordPress のバージョンを表示するには、パラメータとして "version" を指定します:

```php
bloginfo( 'version' );
```

<!--
For each template tag, the parameters differ. A list of the parameters and what they can do can be found on specific template tag pages located throughout the [code reference](https://developer.wordpress.org/reference/).
-->
テンプレートタグごとに、パラメータは異なります。パラメータの一覧とそれぞれのパラメータの役割については[コードリファレンス](https://developer.wordpress.org/reference/)のテンプレートタグのページを確認してください。

<!--
### Using Template Tags Within the Loop
-->
### ループ内でテンプレートタグを使う

<!--
Many template tags work within the [WordPress Loop](https://developer.wordpress.org/themes/basics/the-loop/). This means that they are included in the template files as part of the php “loop” that generates the pages users see based upon the instructions inside of the loop.
-->
多くのテンプレートタグは [WordPress のループ](https://developer.wordpress.org/themes/basics/the-loop/)内で使えます。つまり、テンプレートタグが php の「ループ」の一部としてテンプレートファイルに含まれており、ループ内の実装にもとづいてユーザーが目にするページを生成します。

<!--
The WordPress loop begins with:
-->
WordPress のループは次のコードで始まります:

```php
if ( have_posts() ) :
	while ( have_posts() ) :
		the_post();
```

<!--
Template tags that work within the loop must be in the middle area, before the ending section of the loop below:
-->
ループ内で使用するテンプレートタグは、ループの終わりを示す次のコードまでの間に含める必要があります:

```php
	endwhile;
else :
	_e( 'Sorry, no posts matched your criteria.', 'devhub' );
endif;
```

<!--
Some of template tags that need to be inside of the loop include
-->
ループ内で使用するテンプレートタグには次のものが含まれます:

*   [the\_content()](https://developer.wordpress.org/reference/functions/the_content/)
*   [the\_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)
*   [next\_post()](https://developer.wordpress.org/reference/functions/next_post/)
*   [previous\_post()](https://developer.wordpress.org/reference/functions/previous_post/)

<!--
The main reason why some functions require the loop is because they require the global post object to be set.
-->
これらの関数をループ内で使う必要があるのは、グローバルの投稿オブジェクトに依存するためです。

<!--
If the template tag you want to use doesn’t have to be within the loop
-->
次に示すような、ループの中で使う必要がないテンプレートタグについては、どこでも使うことができます。

*   [wp\_list\_cats()](https://developer.wordpress.org/reference/functions/wp_list_cats/)
*   [wp\_list\_pages()](https://developer.wordpress.org/reference/functions/wp_list_pages/)

<!--
then you can put it in any file you’d like, for instance in the sidebar, header, or footer template files.
-->

<!--
These are functions that typically do not require the global post object.
-->
これらの関数は通常、グローバルの投稿オブジェクトに依存しません。

<!--
## See Also
-->
## 関連項目

<!--
*   [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/)
*   [Complete list of Template Tags](https://developer.wordpress.org/themes/references/list-of-template-tags/)
*   [Plugin API Hooks](_wp_link_placeholder)
-->
*   [条件分岐タグ](https://developer.wordpress.org/themes/basics/conditional-tags/)
*   [テンプレートタグの一覧](https://developer.wordpress.org/themes/references/list-of-template-tags/)
*   [プラグイン API フック](_wp_link_placeholder)
