<!-- 
# Template Files
 -->

# テンプレート・ファイル

<!-- 
Template files are used throughout WordPress themes, but first let’s learn about the terminology.
 -->

テンプレート・ファイルは、WordPress テーマ全体で使用されますが、まずは用語について学びましょう。

<!-- 
## Template Terminology
 -->

## テンプレート用語集

<!-- 
The term “template” is used in different ways when working with WordPress themes:
 -->

WordPress テーマを扱う際、「テンプレート」という用語は、異なる意味で使われます:

<!-- 
*   Templates files exist within a theme and express how your site is displayed.
*   [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) is the logic WordPress uses to decide which theme template file(s) to use, depending on the content being requested.
*   [Page Templates](https://developer.wordpress.org/themes/template-files-section/page-template-files/ "Page Templates") are those that apply to pages, posts, and custom post types to change their look and feel.
 -->

*   テンプレート・ファイルはテーマ内に存在し、あなたのサイトの表現方法を決定します。
*   [テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/) とは、WordPress が要求されたコンテンツに応じて、どのテーマ・テンプレート・ファイルを使用するかを決定するロジックです。
*   [ページ・テンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/ "Page Templates") とは、ページ、投稿、カスタム投稿タイプに適用され、それらのルック・アンド・フィールを変更するものです。

<!-- 
**In classic themes,** [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") are built-in WordPress functions you can use inside a template file to retrieve and display data (such as [`the_title()`](https://developer.wordpress.org/reference/hooks/the_title/ "Function Reference/the title") and [`the_content()`](https://developer.wordpress.org/reference/hooks/the_content/ "Function Reference/the content")).
 -->

**クラシック・テーマでは**、[テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") とは、テンプレート・ファイル内で ([`the_title()`](https://developer.wordpress.org/reference/hooks/the_title/ "Function Reference/the title") や [`the_content()`](https://developer.wordpress.org/reference/hooks/the_content/ "Function Reference/the content") など) データを取得・表示するために使用できる、WordPress の内蔵関数です。

<!-- 
**In block themes,** blocks are used instead of template tags.
 -->

**ブロック・テーマでは**、テンプレート・タグの代わりにブロックが使用されます。

<!-- 
## Template files
 -->

## テンプレート・ファイル

<!-- 
WordPress themes are made up of template files.
 -->

WordPress テーマは、テンプレート・ファイルで構成されています。

<!-- 
*   In classic themes these are PHP files that contain a mixture of HTML, [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags"), and PHP code.
*   In block themes these are HTML files that contain HTML markup representing blocks.
 -->

*   クラシック・テーマでは、これらは HTML、[テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags")、PHP コードが混在する PHP ファイルです。
*   ブロックテーマでは、これらはブロックを表す HTML マークアップを含む、HTML ファイルです。

<!-- 
When you are building your theme, you will use template files to affect the layout and design of different parts of your website. For example, you would use a `header` template or template part to create a header.
 -->

あなたのテーマを構築する際には、あなたの Web サイトのさまざまな部分のレイアウトやデザインに影響を与えるために、テンプレート・ファイルを使用します。たとえば、ヘッダーを作成するには、`header` テンプレートまたはテンプレート・パーツを使用します。

<!-- 
When someone visits a page on your website, WordPress loads a template based on the request. The type of content that is displayed by the template file is determined by the [Post Type](https://developer.wordpress.org/themes/basics/post-types/) associated with the template file. The [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") describes which template file WordPress will load based on the type of request and whether the template exists in the theme. The server then parses the code in the template and returns HTML to the visitor.
 -->

誰かがあなたの Web サイトのページを訪問すると、WordPress はリクエストにもとづいてテンプレートをロードします。テンプレート・ファイルによって表示されるコンテンツの種類は、そのテンプレート・ファイルに関連付けられた [投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/) によって決定されます。[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") は、リクエストの種類とテーマ内にテンプレートが存在するかどうかにもとづいて、WordPress がどのテンプレート・ファイルをロードするかを定義します。その後、サーバーはテンプレート内のコードを解析し、訪問者に対して HTML を返します。

<!-- 
The most critical template file is `the index`, which is the catch-all template if a more-specific template can not be found in the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/). Although a theme only needs a `index` template, typically themes include numerous templates to display different content types and contexts.
 -->

最も重要なテンプレート・ファイルは `the index` です。これは [テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/) 内でより具体的なテンプレートが見つからない場合の、最終的なテンプレートです。テーマには `index` テンプレートのみが必要ですが、通常はさまざまなコンテンツ・タイプやコンテキストを表示するために、多数のテンプレートが含まれます。

<!-- 
## Template partials
 -->

## テンプレート・パーシャル

<!-- 
A template part is a piece of a template that is included as a part of another template, such as a site header. Template part can be embedded in multiple templates, simplifying theme creation. Common template parts include:
 -->

テンプレート・パーツとは、サイトヘッダーなど、別のテンプレートの一部として組み込まれるテンプレートの構成要素です。テンプレート・パーツは複数のテンプレートに埋め込むことができ、テーマ制作を簡素化します。一般的なテンプレート・パーツには、以下が含まれます:

<!-- 
*   `header.php` or `header.html` for generating the site’s header
*   `footer.php` or `footer.html` for generating the footer
*   `sidebar.php` or `sidebar.html` for generating the sidebar
 -->

*   `header.php` または `header.html` サイトのヘッダーの生成用
*   `footer.php` または `footer.html` フッターの生成用
*   `sidebar.php` または `sidebar.html` サイドバーの生成用

<!-- 
While the above template files are special-case in WordPress and apply to just one portion of a page, you can create any number of template partials and include them in other template files.
 -->

上記のテンプレート・ファイルは WordPress における特殊なケースであり、ページの一部にのみ適用されますが、任意の数のテンプレート・パーシャルを作成し、他のテンプレート・ファイルにインクルードできます。

<!-- 
In block themes, template parts must be placed inside a folder called parts.
 -->

ブロック・テーマでは、テンプレート・パーツは「parts」という名前のフォルダー内に保存する必要があります

<!-- 
## Common WordPress template files
 -->

## 一般的な WordPress テンプレート・ファイル

<!-- 
Below is a list of some basic theme templates and files recognized by WordPress.
 -->

以下は、WordPress が認識する、基本的なテーマ・テンプレートとファイルのリストです。

<!-- 
**index.php (classic theme) or index.html (block theme)**
 -->

**index.php (クラシック・テーマ) または、index.html (ブロック・テーマ)**

<!-- 
The main template file. It is **required** in all themes.
 -->

メイン・テンプレート・ファイルです。すべてのテーマで **必須** です。

<!-- 
**style.css**
 -->

**style.css**

<!-- 
The main stylesheet. It is **required** in all themes and contains the information header for your theme.
 -->

メイン・スタイルシートです。すべてのテーマで **必須** であり、あなたのテーマの情報ヘッダーを含みます。

<!-- 
**rtl.css**
 -->

**rtl.css**

<!-- 
The right-to-left stylesheet is included automatically if the website language’s text direction is right-to-left.
 -->

Web サイトの言語のテキスト方向が right-to-left の場合、right-to-left スタイルシートが自動的にインクルードされます。

<!-- 
**front-page.php (classic theme) or front-page.html (block theme)**
 -->

**front-page.php (クラシック・テーマ) または、front-page.html (ブロック・テーマ)**

<!-- 
The front page template is always used as the site front page if it exists, regardless of what settings on **Admin > Settings > Reading**.
 -->

「フロントページ」テンプレートは、**管理画面 > 設定 > 表示設定** での設定にかかわらず、存在する場合、常にサイトのホームページとして使用されます。

<!-- 
**home.php (classic theme) or home.html (block theme)**
 -->

**home.php (クラシック・テーマ) または、home.html (ブロック・テーマ)**

<!-- 
The home page template is the front page by default. If you do not set WordPress to use a static front page, this template is used to show latest posts.
 -->

「ホームページ」テンプレートは、デフォルトでホームページとして機能します。WordPress で静的なホームページを設定しない場合、このテンプレートは、最新の投稿を表示するために使用されます。

<!-- 
**singular.php (classic theme) or singular.html (block theme)**
 -->

**singular.php (クラシック・テーマ) または、singular.html (ブロック・テーマ)**

<!-- 
The singular template is used for posts when `single.php` is not found, or for pages when `page.php` are not found. If `singular.php` is not found, `index.php` is used.
 -->

「個別」テンプレートは、`single.php` が見つからない場合の投稿用に、または `page.php` が見つからない場合の固定ページ用に、使用されます。`singular.php` が見つからない場合、`index.php` が使用されます。

<!-- 
**single.php (classic theme) or single.html (block theme)**
 -->

**single.php (クラシック・テーマ) または、single.html (ブロック・テーマ)**

<!-- 
The single post template is used when a visitor requests a single post.
 -->

訪問者が個別投稿をリクエストした際に、「個別投稿」テンプレートが使用されます。

<!-- 
**single-{post-type}.php (classic theme) or single-{post-type}.html (block theme)**
 -->

**single-{post-type}.php (クラシック・テーマ) または、single-{post-type}.html (ブロック・テーマ)**

<!-- 
The single post template used when a visitor requests a single post from a custom post type. For example, `single-book.php` would be used for displaying single posts from a custom post type named *book*.
 -->

訪問者がカスタム投稿タイプに由来する個別投稿をリクエストした際に、「個別投稿」テンプレートが使用されます。たとえば、`single-book.php` は *book* という名称のカスタム投稿タイプに由来する個別投稿を表示するために使用されます。

<!-- 
**archive-{post-type}.php (classic theme) or archive-{post-type}.html (block theme)**
 -->

**archive-{post-type}.php (クラシック・テーマ) または、archive-{post-type}.html (ブロック・テーマ)**

<!-- 
The archive post type template is used when visitors request a custom post type archive. For example, `archive-books.php` would be used for displaying an archive of posts from the custom post type named *books*. The archive template file is used if the `archive-{post-type} template` is not present.
 -->

訪問者がカスタム投稿タイプのアーカイブをリクエストした際に、「アーカイブ投稿タイプ」テンプレートが使用されます。たとえば、`archive-books.php` は、*books* というカスタム投稿タイプに由来する投稿アーカイブを表示するために使用されます。`archive-{post-type}` テンプレートが存在しない場合に、「アーカイブ」テンプレート・ファイルが使用されます。

<!-- 
**page.php (classic theme) or page.html (block theme)**
 -->

**page.php (クラシック・テーマ) または、page.html (ブロック・テーマ)**

<!-- 
The page template is used when visitors request individual pages, which are a built-in template.
 -->

訪問者が個々のページをリクエストした際に、「ページ」テンプレートが使用される、ビルトインのテンプレートです。

<!-- 
**page-{slug}.php (classic theme) or page-{slug}.html (block theme)**
 -->

**page-{slug}.php (クラシック・テーマ) または、page-{slug}.html (ブロック・テーマ)**

<!-- 
The page slug template is used when visitors request a specific page, for example one with the “about” slug (page-about.php).
 -->

訪問者が特定のページ、たとえば、「about」スラッグを持つページ (page-about.php) をリクエストした際に、「ページ・スラッグ」テンプレートが使用されます。

<!-- 
**category.php (classic theme) or category.html (block theme)**
 -->

**category.php (クラシック・テーマ) または、category.html (ブロック・テーマ)**

<!-- 
The category template is used when visitors request posts by category.
 -->

訪問者がカテゴリー別に投稿をリクエストした際に、「カテゴリー」テンプレートが使用されます。

<!-- 
**tag.php (classic theme) or tag.html (block theme)**
 -->

**tag.php (クラシック・テーマ) または、tag.html (ブロック・テーマ)**

<!-- 
The tag template is used when visitors request posts by tag.
 -->

訪問者がタグで投稿をリクエストした際に、「タグ」テンプレートが使用されます。

<!-- 
**taxonomy.php (classic theme) or taxonomy.html (block theme)**
 -->

**taxonomy.php (クラシック・テーマ) または、taxonomy.html (ブロック・テーマ)**

<!-- 
The taxonomy term template is used when a visitor requests a term in a custom taxonomy.
 -->

訪問者がカスタム・タクソノミーのタームをリクエストした際に、「タクソノミー・ターム」テンプレートが使用されます。

<!-- 
**author.php (classic theme) or author.html (block theme)**
 -->

**author.php (クラシック・テーマ) または、author.html (ブロック・テーマ)**

<!-- 
The author page template is used whenever a visitor loads an author page.
 -->

訪問者が作者ページをロードする際には、「作者ページ」テンプレートが常に使用されます。

<!-- 
**date.php (classic theme) or date.html (block theme)**
 -->

**date.php (クラシック・テーマ) または、date.html (ブロック・テーマ)**

<!-- 
The date/time template is used when posts are requested by date or time. For example, the pages generated with these slugs:  
http://example.com/blog/2014/  
http://example.com/blog/2014/05/  
http://example.com/blog/2014/05/26/
 -->

投稿を日付または時刻でリクエストした際に、「日付/時刻」テンプレートが使用されます。たとえば、以下のスラッグで生成されたページ: 
http://example.com/blog/2014/  
http://example.com/blog/2014/05/  
http://example.com/blog/2014/05/26/

<!-- 
**archive.php (classic theme) or archive.html (block theme)**
 -->

**archive.php (クラシック・テーマ) または、archive.html (ブロック・テーマ)**

<!-- 
The archive template is used when visitors request posts by category, author, or date. **Note**: this template will be overridden if more specific templates are present like `category.php`, `author.php`, and `date.php`.
 -->

訪問者がカテゴリー、作者、または日付で投稿をリクエストした際に、「アーカイブ」テンプレートが使用されます。**注**: `category.php`、`author.php` および `date.php` など、より具体的なテンプレートが存在する場合、本テンプレートは上書きされます。

<!-- 
**search.php (classic theme) or search.html (block theme)**
 -->

**search.php (クラシック・テーマ) または、search.html (ブロック・テーマ)**

<!-- 
The search results template is used to display a visitor’s search results.
 -->

訪問者の検索結果を表示するために、「検索結果」テンプレートが使用されます。

<!-- 
**attachment.php (classic theme) or attachment.html (block theme)**
 -->

**attachment.php (クラシック・テーマ) または、attachment.html (ブロック・テーマ)**

<!-- 
The attachment template is used when viewing a single attachment like an image, pdf, or other media file.
 -->

画像、PDF、その他のメディア・ファイルなどの個別の添付ファイルを表示する際に、「添付ファイル」テンプレートが使用されます。

<!-- 
**image.php (classic theme) or image.html (block theme)**
 -->

**image.php (クラシック・テーマ) または、image.html (ブロック・テーマ)**

<!-- 
The image attachment template is a more specific version of `attachment.php` and is used when viewing a single image attachment. If not present, WordPress will use `attachment.php` instead.
 -->

単一の画像添付を表示する際に、`attachment.php` のより具体的なバージョン、「画像添付」テンプレートが使用されます。存在しない場合、WordPress は代わりに `attachment.php` を使用します。

<!-- 
**404.php (classic theme) or 404.html (block theme)**
 -->

**404.php (クラシック・テーマ) または、404.html (ブロック・テーマ)**

<!-- 
The 404 template is used when WordPress cannot find a post, page, or other content that matches the visitor’s request.
 -->

WordPress が訪問者のリクエストに合致する投稿、ページ、その他のコンテンツを見つけられない場合に、「404」テンプレートが使用されます。

<!-- 
**comments.php**
 -->

**comments.php**

<!-- 
The comments template in classic themes. In block themes, blocks are used instead.
 -->

クラシック・テーマでの、「コメント」テンプレートです。ブロック・テーマでは、代わりにブロックが使用されます。

<!-- 
## Using template files
 -->

## テンプレート・ファイルの使用

<!-- 
### Classic themes
 -->

### クラシック・テーマ

<!-- 
In classic themes, within WordPress templates, you can use [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") to display information dynamically, include other template files, or otherwise customize your site.
 -->

クラシック・テーマでは、WordPress テンプレート内で [テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") を使用して、情報を動的に表示したり、他のテンプレート・ファイルをインクルードしたり、あなたのサイトをカスタマイズできます。

<!-- 
For example, in your `index.php` you can include other files in your final generated page:
 -->

たとえば、あなたの `index.php` では、あなたの最終的に生成されるページに、他のファイルをインクルードできます:

<!-- 
*   To include the header, use [get\_header()](https://developer.wordpress.org/reference/functions/get_header/ "Function Reference/get header")
*   To include the sidebar, use [get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/ "Function Reference/get sidebar")
*   To include the footer, use [get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/ "Function Reference/get footer")
*   To include the search form, use [get\_search\_form()](https://developer.wordpress.org/reference/functions/get_search_form/ "Function Reference/get search form")
*   To include custom theme files, use [get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/ "Function Reference/get template part")
 -->

*   ヘッダーをインクルードするには、[get\_header()](https://developer.wordpress.org/reference/functions/get_header/ "Function Reference/get header") を使用します
*   サイドバーをインクルードするには、[get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/ "Function Reference/get sidebar") を使用します
*   フッターをインクルードするには、[get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/ "Function Reference/get footer") を使用します
*   検索フォームをインクルードするには、[get\_search\_form()](https://developer.wordpress.org/reference/functions/get_search_form/ "Function Reference/get search form") を使用します
*   カスタム・テーマ・ファイルをインクルードするには、[get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/ "Function Reference/get template part") を使用します

<!-- 
Here is an example of WordPress template tags to *include* specific templates into your page:
 -->

以下に、WordPress テンプレート・タグを使用して、特定のテンプレートをあなたのページに *インクルード* する例を示します:

```php
<?php get_sidebar(); ?>
<?php get_template_part( 'featured-content' ); ?>
<?php get_footer(); ?>
```

<!-- 
There’s an entire page on [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") that you can dive into to learn all about them.
 -->

[テンプレート・タグ](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") について詳しく学ぶための専用ページが、用意されています。

<!-- 
Refer to the section [Linking Theme Files & Directories](https://developer.wordpress.org/themes/basics/linking-theme-files-directories/ "Linking Theme Files & Directories") for more information on linking component templates.
 -->

「コンポーネント」テンプレートのリンクに関する詳細は、[テーマ・ファイル & ディレクトリのリンク](https://developer.wordpress.org/themes/basics/linking-theme-files-directories/ "Linking Theme Files & Directories") セクションをご覧ください。

<!-- 
### Block themes
 -->

### ブロック・テーマ

<!-- 
In block themes you use blocks instead of template tags. Block markup is the HTML code that WordPress uses to display the block. Template parts are blocks, and you add them to your template files the same way as you add blocks.
 -->

ブロック・テーマでは、テンプレート・タグの代わりにブロックを使用します。ブロック・マークアップとは、WordPress がブロックを表示するために使用する、HTML コードです。テンプレート・パーツはブロックであり、ブロックを追加するのと同じ方法で、あなたのテンプレート・ファイルに追加します。

<!-- 
To include a header or footer template part, add the block markup for the template part. The `slug` is the name of the part. If the file you want to include is called `header.html`, then the slug is “header”:
 -->

ヘッダーまたはフッターのテンプレート・パーツをインクルードするには、テンプレート用のブロック・マークアップを追加します。`slug` はパーツの名称です。インクルードしたいファイル名が `header.html` の場合、slug は「header」になります:

```markup
<!-- wp:template-part {"slug":"header"} /-->
(your page content)
<!-- wp:template-part {"slug":"footer"} /-->
```

<!-- 
To include the search form, use the block markup for the search block:
 -->

検索フォームを含めるには、検索ブロック用のブロック・マークアップを使用します:

```markup
<!-- wp:search {"label":"Search","buttonText":"Search"} /-->
```