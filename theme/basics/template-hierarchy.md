<!-- 
# Template Hierarchy
-->
# テンプレート階層

<!-- 
As discussed, [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template files page") are modular, reusable files, used to generate the web pages on your WordPress site. Some template files (such as the header and footer template) are used on all of your site’s pages, while others are used only under specific conditions.
-->
前述のとおり、[テンプレートファイル](https://developer.wordpress.org/themes/basics/template-files/ "テンプレートファイルのページ")は、モジュール式の再利用可能なファイルで、WordPress サイトの Web ページを生成するために使用されます。テンプレートファイルには、ヘッダーやフッターのテンプレートなど、サイトのすべてのページで使用されるものと、特定の条件下でのみ使用されるものがあります。

<!-- 
This article explains **how WordPress determines which template file(s) to use on individual pages**. If you want to customize an existing WordPress theme it will help you decide which template file needs to be edited.
-->
この記事では、**WordPress が個々のページで使用するテンプレートファイルを決定する方法**について説明します。既存の WordPress テーマをカスタマイズしたい場合に、どのテンプレートファイルを編集する必要があるかを判断するのに役立ちます。

<!-- 
Tip: You can also use [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags") to control which templates are loaded on a specific page.
-->
ヒント：[条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/ "条件付きタグ")を使って、特定のページでどのテンプレートを読み込むかをコントロールすることもできます。

<!-- 
## The Template File Hierarchy
-->
## テンプレートファイル階層

<!-- 
### Overview
-->
### 概要

<!-- 
WordPress uses the [query string](https://wordpress.org/support/article/glossary/#query-string) to decide which template or set of templates should be used to display the page. The query string is information that is contained in the link to each part of your website.
-->
WordPress は、[クエリ文字列](https://wordpress.org/support/article/glossary/#query-string) を使用して、どのテンプレートまたはテンプレートのセットを使用してページを表示するかを決定します。クエリ文字列はウェブサイトの各部分へのリンクに含まれる情報です。

<!-- 
Put simply, WordPress searches down through the template hierarchy until it finds a matching template file. To determine which template file to use, WordPress:
-->
簡単に言うと、WordPress はテンプレートの階層を検索して、一致するテンプレートファイルを見つけるのです。以下のような手順で WordPress はどのテンプレートファイルを使用するかを決定します。

<!-- 
1.  Matches every query string to a query type to decide which page is being requested (for example, a search page, a category page, etc);
2.  Selects the template in the order determined by the template hierarchy;
3.  Looks for template files with specific names in the current theme’s directory and uses the **first matching template file** as specified by the hierarchy.
-->
1.  すべてのクエリ文字列をクエリタイプにマッチさせ、どのページがリクエストされているかを判断します（例：検索ページ、カテゴリページなど）。
2.  テンプレート階層で決められた順序によりテンプレートを選択します。
3.  現在のテーマのディレクトリ内で特定の名前のテンプレートファイルを探し、階層で指定された**最初にマッチするテンプレートファイル**を使用します。

<!-- 
With the exception of the basic `index.php` template file, you can choose whether you want to implement a particular template file or not.
-->
基本的な `index.php` テンプレートファイルを例外として、特定のテンプレートファイルを実装するかどうかを選択できます。

Tip: In these examples, the PHP file extension is used. In block themes, HTML files are used instead, but the template hierarchy is the same.

If WordPress cannot find a template file with a matching name, it will skip to the next file in the hierarchy. If WordPress cannot find any matching template file, the theme’s `index.php` file will be used.

<!-- 
If WordPress cannot find a template file with a matching name, it will skip to the next file in the hierarchy. If WordPress cannot find any matching template file, the theme’s `index.php` file will be used.
-->
一致する名前のテンプレートファイルが見つからない場合、WordPress は次の階層のファイルにスキップします。一致するテンプレートファイルが何も見つからない場合は、テーマの `index.php` ファイルが使用されます。

<!--
When you are using a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/), any file you add to your child theme will over-ride the same file in the parent theme. For example, both themes contain the same template `category.php`, then child theme’s template is used.  
If a child theme contains the specific template such as `category-unicorns.php` and the parent theme contains lower prioritized template such as `category.php`, then child theme’s `category-unicorns.php` is used.  
Contrary, if a child theme contains general template only such as `category.php` and the parent theme contains the specific one such as `category-unicorns.php`, then parent’s template `category-unicorns.php` is used.
-->
[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/)を使用している場合、子テーマに追加したファイルは、親テーマの同じファイルよりも優先されます。例えば、両方のテーマに同じテンプレート `category.php` がある場合、子テーマのテンプレートが使われます。 
子テーマが `category-unicorns.php` のような特定のテンプレートを含み、親テーマが `category.php` のような優先順位の低いテンプレートを含む場合、子テーマの `category-unicorns.php` が使用されます。 
逆に、子テーマが `category.php` のような一般的なテンプレートのみを含み、親テーマが `category-unicorns.php` のような特定のテンプレートを含む場合は、親テーマのテンプレート `category-unicorns.php` が使用されます。

<!--
### Examples
-->
### 例

<!--
If your blog is at `http://example.com/blog/` and a visitor clicks on a link to a category page such as `http://example.com/blog/category/your-cat/`, WordPress looks for a template file in the current theme’s directory that matches the category’s ID to generate the correct page. More specifically, WordPress follows this procedure:
-->
例えば、ブログの URL が`http://example.com/blog/`だとして、(ブログの)訪問者が`http://example.com/blog/category/your-cat/`などのカテゴリーページへのリンクをクリックしたとします。この時 WordPress はテーマのディレクトリ内でカテゴリーの ID に一致するテンプレートファイルを探し、正しいページを生成します。より具体的にいうと、WordPress は次の順に従います。

<!--
1.  Looks for a template file in the current theme’s directory that matches the category’s slug. If the category slug is “unicorns,” then WordPress looks for a template file named `category-unicorns.php`.
2.  If `category-unicorns.php` is missing and the category’s ID is 4, WordPress looks for a template file named `category-4.php`.
3.  If `category-4.php` is missing, WordPress will look for a generic category template file, `category.php`.
4.  If `category.php` does not exist, WordPress will look for a generic archive template, `archive.php`.
5.  If `archive.php` is also missing, WordPress will fall back to the main theme template file, `index.php`.
-->
1.  現在のテーマのディレクトリ内で、カテゴリーのスラッグに一致するテンプレートファイルを探します。もしカテゴリーのスラッグが「unicorns」であれば、WordPress は `category-unicorns.php` という名前のテンプレートファイルを探します。
2. `category-unicorns.php` がなく、カテゴリの ID が 4 の場合、WordPress は `category-4.php` という名前のテンプレートファイルを探します。
3. `category-4.php` がない場合、WordPress は一般的なカテゴリーのテンプレートファイルである `category.php` を探します。
4. `category.php` が存在しない場合、WordPress は一般的なアーカイブのテンプレートである `archive.php` を探します。
5. `archive.php` も見つからない場合、WordPress はテーマのメインテンプレートファイルである `index.php` で処理します。

<!-- 
### Visual Overview
-->
### 外観図
<!-- 
The following diagram shows which template files are called to generate a WordPress page based on the WordPress template hierarchy.
-->
以下の図では、WordPress のテンプレート階層に基づいて、どのテンプレートファイルが呼び出されて WordPress のページが生成されるかを表しています。
[![](https://developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04-1024x639.png)](https://developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png)

<!-- 
You can also [interact with this diagram](http://wphierarchy.com/).
-->
または[対話式バージョン](http://wphierarchy.com/)もあります。

<!--
## The Template Hierarchy In Detail
-->
## テンプレート階層の詳細

<!-- 
While the template hierarchy is easier to understand as a diagram, the following sections describe the order in which template files are called by WordPress for a number of query types.
-->
テンプレートの階層は図で見るとわかりやすいのですが、以下のセクションでは、いくつかのクエリタイプに対して WordPress からテンプレートファイルが呼び出される順番を説明します。

<!-- 
### Home Page display
-->
### ホームページ表示

<!-- 
By default, WordPress sets your site’s home page to display your latest blog posts. This page is called the blog posts index. You can also set your blog posts to display on a separate static page. The template file `home.php` is used to render the blog posts index, whether it is being used as the front page or on separate static page. If `home.php` does not exist, WordPress will use `index.php`.
-->
WordPress のデフォルトでは、サイトのトップページに最新のブログ投稿が表示されるように設定されています。このページをブログ投稿インデックスと呼びます。また、ブログ投稿を別の固定ページに表示するように設定することもできます。ブログ投稿インデックスの表示には、テンプレートファイル `home.php` が使用されますが、これはフロントページとして使用する場合も、別の固定ページとして使用する場合も同じです。`home.php` が存在しない場合、WordPress は `index.php` を使用します。

1.  `home.php`
2.  `index.php`

<!--
Note: If `front-page.php` exists, it will override the `home.php` template.
-->
注意: `front-page.php` が存在する場合は、 `home.php` テンプレートに優先します。

<!-- 
### Front Page display
-->
### フロントページ表示

<!--
The `front-page.php` template file is used to render your site’s front page, whether the front page displays the blog posts index (mentioned above) or a static page. The front page template takes precedence over the blog posts index (`home.php`) template. If the `front-page.php` file does not exist, WordPress will either use the `home.php` or `page.php` files depending on the setup in Settings → Reading. If neither of those files exist, it will use the `index.php` file.
-->
`front-page.php` テンプレートファイルはサイトのフロントページの表示に使用されます。フロントページは(上述の)ブログ投稿インデックスか、固定ページを表示します。フロントページのテンプレートは、ブログ投稿インデックス（`home.php`）のテンプレートよりも優先されます。`front-page.php` ファイルが存在しない場合、WordPress は 設定 > 表示設定 での設定に応じて `home.php` または `page.php` ファイルを使用します。もしこれらのファイルがどちらも存在しない場合は、`index.php` ファイルを使用します。

<!--
1.  `front-page.php` – Used for both “**your latest posts**” or “**a static page**” as set in the **front page displays** section of Settings → Reading.
2.  `home.php` – If WordPress cannot find `front-page.php` and “**your latest posts**” is set in the **front page displays** section, it will look for `home.php`. Additionally, WordPress will look for this file when the **posts page** is set in the **front page displays** section.
3.  `page.php` – When “**front page**” is set in the **front page displays** section.
4.  `index.php` – When “**your latest posts**” is set in the **front page displays** section but `home.php` does not exist *or* when **front page** is set but `page.php` does not exist.
-->

1. `front-page.php` - 設定 > 表示設定 セクションで「**フロントページの表示**」が「**最新の投稿**」または「**固定ページ**」どちらになっている場合でも使われます。
2. `home.php` - WordPress が `front-page.php` を見つけられず、且つ「**フロントページの表示**」セクションで「**最新の投稿**」が設定されている場合、`home.php` を参照します。加えて、WordPress は「**フロントページの表示**」セクションで「**投稿ページ**」が設定されている場合にもこのファイルを参照します。
3. `page.php` – 「**フロントページの表示**」セクションで**フロントページ**が設定されている場合。
4. `index.php` – 「**フロントページの表示**」セクションで「**最新の投稿**」が設定されており、且つ `home.php` が存在しない場合。または**フロントページ**が設定されているが `page.php` が存在しない場合。

<!--
As you can see, there are a lot of rules to what path WordPress takes. Using the chart above is the best way to determine what WordPress will display.
-->
このように、WordPressがどのような経路をとるかには多くのルールがあります。上の図を使用することは、WordPress が何を表示するかを特定する最良の方法です。

<!--
### Privacy Policy Page display
-->
### プライバシーポリシーページ表示

<!--
The `privacy-policy.php` template file is used to render your site’s Privacy Policy page. The Privacy Policy page template takes precedence over the static page (`page.php`) template. If the `privacy-policy.php` file does not exist, WordPress will either use the `page.php` or `singular.php` files depending on the available templates. If neither of those files exist, it will use the `index.php` file.
-->
`privacy-policy.php` テンプレートファイルは、あなたのサイトのプライバシーポリシーページをレンダリングするために使われます。プライバシーポリシーページのテンプレートは、静的ページ（`page.php`）のテンプレートよりも優先されます。`privacy-policy.php` ファイルが存在しない場合、WordPress は利用可能なテンプレートに応じて `page.php` または `singular.php` ファイルを使用します。これらのファイルが存在しない場合は、`index.php`ファイルを使用します。

<!--
1.  `privacy-policy.php` – Used for the Privacy Policy page set in the **Change your Privacy Policy page** section of Settings → Privacy.
2.  `custom template file` – The [page template](https://developer.wordpress.org/themes/template-files-section/page-template-files/) assigned to the page. See `get_page_templates()`.
3.  `page-{slug}.php` – If the page slug is `privacy`, WordPress will look to use `page-privacy.php`.
4.  `page-{id}.php` – If the page ID is 6, WordPress will look to use `page-6.php`.
5.  `page.php`
6.  `singular.php`
7.  `index.php`
-->
1.  `privacy-policy.php` – 「設定」→「プライバシー」の「**プライバシーポリシーページの変更**」で設定したプライバシーポリシーページに使用されます。
2.  `カスタムテンプレートファイル` – ページに割り当てられた[ページテンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/)です。詳しくは `get_page_templates()` をご覧ください。
3.  `page-{slug}.php` – ページスラッグが `privacy` の場合、WordPress は `page-privacy.php` の使用を検討します。
4.  `page-{id}.php` – ページ ID が 6 の場合、WordPressは `page-6.php` を使おうとします。
5.  `page.php`
6.  `singular.php`
7.  `index.php`

<!--
### Single Post
-->
### 個別投稿

<!--
The single post template file is used to render a single post. WordPress uses the following path:
-->
個別投稿のテンプレートファイルは、1 つの投稿を表示するために使用されます。WordPress では、以下の順で表示されます:

<!--
1.  `single-{post-type}-{slug}.php` – (Since 4.4) First, WordPress looks for a template for the specific post. For example, if [post type](https://developer.wordpress.org/themes/basics/post-types/) is `product` and the post slug is `dmc-12`, WordPress would look for `single-product-dmc-12.php`.
2.  `single-{post-type}.php` – If the post type is `product`, WordPress would look for `single-product.php`.
3.  `single.php` – WordPress then falls back to `single.php`.
4.  `singular.php` – Then it falls back to `singular.php`.
5.  `index.php` – Finally, as mentioned above, WordPress ultimately falls back to `index.php`.
-->
1.  `single-{post-type}-{slug}.php` – まず、WordPress は特定の記事のテンプレートを探します(4.4 以降) 。例えば、[投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/)が `product` で、記事のスラッグが `dmc-12` の場合、WordPress は `single-product-dmc-12.php` を探します。
2.  `single-{post-type}.php` – 投稿タイプが `product` であれば、WordPress は `single-product.php` を探します。
3.  `single.php` – 次に WordPress は `single.php` へフォールバックします。
4.  `singular.php` – その次に `singular.php` へフォールバックします。
5.  `index.php` – 最終的には、前述のとおり、WordPress は `index.php` へフォールバックします。

<!-- 
### Single Page
-->
### 個別ページ

<!--
The template file used to render a static page (`page` post-type). Note that unlike other post-types, `page` is special to WordPress and uses the following path:
-->
個別ページ（`page` 投稿タイプ）をレンダリングするために使用されるテンプレートファイルです。他の投稿タイプとは異なり、`page` は WordPress 特有のもので、以下の順で表示されることに注意してください。

<!--
1.  `custom template file` – The [page template](https://developer.wordpress.org/themes/template-files-section/page-template-files/) assigned to the page. See `[get_page_templates()](https://developer.wordpress.org/reference/functions/get_page_templates/)`.
2.  `page-{slug}.php` – If the page slug is `recent-news`, WordPress will look to use `page-recent-news.php`.
3.  `page-{id}.php` – If the page ID is 6, WordPress will look to use `page-6.php`.
4.  `page.php`
5.  `singular.php`
6.  `index.php`
-->
1.  `カスタムテンプレートファイル` - ページに割り当てられた[ページテンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/)です。[get_page_templates()](https://developer.wordpress.org/reference/functions/get_page_templates/)`を参照してください。
2.  `page-{slug}.php` – ページスラッグが `recent-news` の場合、WordPress は `page-recent-news.php` を使用しようとします。
3.  `page-{id}.php` – ページ ID が6の場合、WordPress は `page-6.php` を使おうとします。
4.  `page.php`
5.  `singular.php`
6.  `index.php`

<!-- 
### Category
-->
### カテゴリー

<!-- 
Rendering category archive index pages uses the following path in WordPress:
-->
カテゴリーアーカイブインデックスページは、WordPressでは以下の順で表示されます。

<!--
1.  `category-{slug}.php` – If the category’s slug is `news`, WordPress will look for `category-news.php`.
2.  `category-{id}.php` – If the category’s ID is `6`, WordPress will look for `category-6.php`.
3.  `category.php`
4.  `archive.php`
5.  `index.php`
-->
1. `category-{slug}.php` – カテゴリーのスラッグが `news` ならば WordPress は `category-news.php` を探します。
2. `category-{id}.php` – カテゴリー ID が `6` ならば WordPress は `category-6.php` を探します。
3.  `category.php`
4.  `archive.php`
5.  `index.php`

<!--
### Tag
-->
### タグ

<!-- 
To display a tag archive index page, WordPress uses the following path:
-->
タグアーカイブインデックスページは、WordPress では以下の順で表示されます。

<!-- 
1.  `tag-{slug}.php` – If the tag’s slug is `sometag`, WordPress will look for `tag-sometag.php`.
2.  `tag-{id}.php` – If the tag’s ID is `6`, WordPress will look for `tag-6.php`.
3.  `tag.php`
4.  `archive.php`
5.  `index.php`
-->
1. `tag-{slug}.php` – タグのスラッグが `sometag` ならば WordPress は `tag-sometag.php` を探します。
2. `tag-{id}.php` – タグの ID が `6` ならば WordPress は `tag-6.php` を探します。
3.  `tag.php`
4.  `archive.php`
5.  `index.php`

<!-- 
### Custom Taxonomies
-->
### カスタムタクソノミー

<!-- 
[Custom taxonomies](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) use a slightly different template file path:
-->
[カスタムタクソノミー](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/)は少し異なる順で表示されます。

<!--
1.  `taxonomy-{taxonomy}-{term}.php` – If the taxonomy is `sometax`, and taxonomy’s term is `someterm`, WordPress will look for `taxonomy-sometax-someterm.php.` In the case of [post formats](https://developer.wordpress.org/themes/functionality/post-formats/), the taxonomy is ‘post\_format’ and the terms are ‘post-format-{format}. i.e. `taxonomy-post_format-post-format-link.php` for the link post format.
2.  `taxonomy-{taxonomy}.php` – If the taxonomy were `sometax`, WordPress would look for `taxonomy-sometax.php`.
3.  `taxonomy.php`
4.  `archive.php`
5.  `index.php`
-->
1. `taxonomy-{taxonomy}-{term}.php` – タクソノミーが `sometax`、タクソノミーの用語が `someterm` ならば WordPress は `taxonomy-sometax-someterm.php` を探します。[投稿フォーマット](https://developer.wordpress.org/themes/functionality/post-formats/)の場合、タクソノミーは 'post_format'、タクソノミーの用語は 'post_format-{format}' です。つまりリンク投稿フォーマットだと `taxonomy-post_format-post-format-link.php` となります。
2.  `taxonomy-{taxonomy}.php` – タクソノミーが `sometax` ならば WordPress は `taxonomy-sometax.php` を探します。
3.  `taxonomy.php`
4.  `archive.php`
5.  `index.php`

<!-- 
### Custom Post Types
-->
### カスタム投稿タイプ

<!-- 
[Custom Post Types](https://developer.wordpress.org/themes/basics/post-types/) use the following path to render the appropriate archive index page.
-->
[カスタム投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/)は以下の順で、適切なアーカイブインデックスページを表示します。

<!-- 
1.  `archive-{post_type}.php` – If the post type is `product`, WordPress will look for `archive-product.php`.
2.  `archive.php`
3.  `index.php`
-->
1. `archive-{post_type}.php` – 投稿タイプが `product` ならば WordPress は `archive-product.php` を探します。
2.  `archive.php`
3.  `index.php`

<!-- 
(For rendering a single post type template, refer to the [single post display](#single-post "Single Post Display") section above.)
-->
(投稿タイプの個別投稿のテンプレートの表示については、上記の[個別投稿](#single-post "個別投稿")の項を参照してください。)

<!-- 
### Author display
-->
### 投稿者表示

<!-- 
Based on the above examples, rendering author archive index pages is fairly explanatory:
-->
上記の例から、投稿者アーカイブのインデックスページの表示は、かなり説明的です。

<!-- 
1.  `author-{nicename}.php` – If the author’s nice name is `matt`, WordPress will look for `author-matt.php`.
2.  `author-{id}.php` – If the author’s ID were `6`, WordPress will look for `author-6.php`.
3.  `author.php`
4.  `archive.php`
5.  `index.php`
-->
1. `author-{nicename}.php` – 投稿者のニックネームが `matt` ならば WordPress は `author-matt.php` を探します。
2. `author-{id}.php` – 投稿者の ID が `6` ならば WordPress は `author-6.php` を探します。
3.  `author.php`
4.  `archive.php`
5.  `index.php`

<!--
### Date
-->
### 日付

<!-- 
Date-based archive index pages are rendered as you would expect:
-->
日付別アーカイブインデックスページは、以下の順に表示されます。

<!-- 
1.  `date.php`
2.  `archive.php`
3.  `index.php`
-->
1.  `date.php`
2.  `archive.php`
3.  `index.php`

<!-- 
### Search Result
-->
### 検索結果

<!-- 
Search results follow the same pattern as other template types:
-->
検索結果は、他のテンプレートタイプと同じパターンで表示されます。

<!-- 
1.  `search.php`
2.  `index.php`
-->
1.  `search.php`
2.  `index.php`

<!-- 
### 404 (Not Found)
-->
### 404 (Not Found) 

<!-- 
Likewise, 404 template files are called in this order:
-->
同様に、404テンプレートファイルも以下の順で呼び出されます。

<!-- 
1.  `404.php`
2.  `index.php`
-->
1.  `404.php`
2.  `index.php`

<!-- 
### Attachment
-->
### 添付ファイル

<!-- 
Rendering an attachment page (`attachment` post-type) uses the following path:
-->
添付ファイルページ（`attachment` 投稿タイプ）は、以下の順で表示されます。

<!-- 
1.  `{MIME-type}.php` – can be any [MIME type](http://en.wikipedia.org/wiki/Internet_media_type "http://en.wikipedia.org/wiki/Internet_media_type") (For example: `image.php`, `video.php`, `pdf.php`). For `text/plain`, the following path is used (in order):
    1.  `text-plain.php`
    2.  `plain.php`
    3.  `text.php`
2.  `attachment.php`
3.  `single-attachment-{slug}.php` – For example, if the attachment slug is `holiday`, WordPress would look for `single-attachment-holiday.php`.
4.  `single-attachment.php`
5.  `single.php`
6.  `singular.php`
7.  `index.php`
-->
1. `{MIME-type}.php` – 任意の[MIME タイプ（メディアタイプ）](https://ja.wikipedia.org/wiki/%E3%83%A1%E3%83%87%E3%82%A3%E3%82%A2%E3%82%BF%E3%82%A4%E3%83%97) (例: `image.php`, `video.php`, `pdf.php`)。`text/plain` ならば以下の順で表示されます。
    1.  `text-plain.php`
    2.  `plain.php`
    3.  `text.php`
2. `attachment.php`
3. `single-attachment-{slug}.php` – 例えば、添付ファイルのスラッグが `holiday` であれば、WordPress は `single-attachment-holiday.php` を探します。
4. `single-attachment.php`
5. `single.php`
6. `singular.php`
7. `index.php`

<!-- 
### Embeds
-->
### 埋め込み

<!-- 
The embed template file is used to render a post which is being embedded. Since 4.5, WordPress uses the following path:
-->
埋め込みテンプレートファイルは、埋め込み対象の記事を表示するために使用されます。4.5 以降、WordPress は以下の順で表示します。

<!-- 
1.  `embed-{post-type}-{post_format}.php` – First, WordPress looks for a template for the specific post. For example, if its post type is `post` and it has the audio format, WordPress would look for `embed-post-audio.php`.
2.  `embed-{post-type}.php` – If the post type is `product`, WordPress would look for `embed-product.php`.
3.  `embed.php` – WordPress then falls back to embed`.php`.
4.  Finally, WordPress ultimately falls back to its own `wp-includes/theme-compat/embed.php` template.
-->
1. `embed-{post-type}-{post_format}.php` – まず、WordPressは特定の投稿のためのテンプレートを探します。例えば、投稿タイプが `post` で、オーディオ形式であれば、WordPress は `embed-post-audio.php` を探します。
2. `embed-{post-type}.php` – 投稿タイプが `product` ならば WordPress は `embed-product.php` を探します。
3. `embed.php` – 次に WordPress は `embed.php` をフォールバックとします。
4. 最終的に、WordPress は自身のテンプレートである `wp-includes/theme-compat/embed.php` をフォールバックとします。

<!-- 
## Non-ASCII Character Handling
-->
## 非 ASCII 文字の取り扱い

<!-- 
Since WordPress 4.7, any dynamic part of a template name which includes non-ASCII characters in its name actually supports both the un-encoded and the encoded form, in that order. You can choose which to use.
-->
WordPress 4.7以降、テンプレート名の動的部分に非 ASCII 文字が含まれている場合、実際にはエンコードされていない形式とエンコードされた形式の両方を順にサポートしています。どちらを使うか選択することができます。

<!-- 
Here’s the page template hierarchy for a page named “Hello World 😀” with an ID of `6`:
-->
以下は、IDが `6` である "Hello World 😀" という名前のページのテンプレート階層です。

*   `page-hello-world-😀.php`
*   `page-hello-world-%f0%9f%98%80.php`
*   `page-6.php`
*   `page.php`
*   `singular.php`

<!-- 
The same behaviour applies to post slugs, term names, and author nicenames.
-->
投稿スラッグ、ターム名、投稿者のニックネームも同じ動作になります。

<!-- 
## Filter Hierarchy
-->
## 階層のフィルター

<!-- 
The WordPress template system lets you filter the hierarchy. This means that you can insert and change things at specific points of the hierarchy. The filter (located in the [`get_query_template()`](https://developer.wordpress.org/reference/functions/get_query_template/) function) uses this filter name: `"{$type}_template"` where `$type` is the template type.
-->
WordPressのテンプレートシステムでは、階層にフィルターを適用できます。つまり、階層の特定のポイントに何かを挿入したり、変更したりすることができるのです。フィルター（[`get_query_template()`](https://developer.wordpress.org/reference/functions/get_query_template/)関数にあります）は、以下のフィルター名を使用します： `"{$type}_template"` ここで `$type` はテンプレートタイプを表します。

<!-- 
Here is a list of all available filters in the template hierarchy:
-->
以下に、テンプレート階層で利用可能なすべてのフィルタの一覧を示します。

*   `embed_template`
*   `404_template`
*   `search_template`
*   `frontpage_template`
*   `home_template`
*   `privacypolicy_template`
*   `taxonomy_template`
*   `attachment_template`
*   `single_template`
*   `page_template`
*   `singular_template`
*   `category_template`
*   `tag_template`
*   `author_template`
*   `date_template`
*   `archive_template`
*   `index_template`

<!-- 
### Example
-->
### 例

<!-- 
For example, let’s take the default author hierarchy:
-->
例として、デフォルトの作成者別での階層を以下に挙げてみます。

*   `author-{nicename}.php`
*   `author-{id}.php`
*   `author.php`

<!-- 
To add `author-{role}.php` before `author.php`, we can manipulate the actual hierarchy using the ‘author_template’ template type. This allows a request for /author/username where username has the role of editor to display using author-editor.php if present in the current themes directory. 
-->
ここで `author-{role}.php` を `author.php` の前に追加するには、'author_template' テンプレートタイプを使用して実際の階層を操作することができます。これにより、/author/username へのリクエストがあった時 username が編集者の権限を持つ場合に、現在のテーマディレクトリに author-editor.php があれば表示することができます。

```
function author_role_template( $templates = '' ) { 
    $author = get_queried_object(); 
    $role = $author->roles[0];

    if ( ! is_array( $templates ) && ! empty( $templates ) ) { 
        $templates = locate_template( array( "author-$role.php", $templates ), false ); 
    } elseif ( empty( $templates ) ) { 
        $templates = locate_template( "author-$role.php", false ); 
    } else { 
        $new_template = locate_template( array( "author-$role.php" ) );

        if ( ! empty( $new_template ) ) { 
            array_unshift( $templates, $new_template ); 
        } 
    } 
    return $templates; 
} 

add_filter( 'author_template', 'author_role_template' );
```

Changelog:

*   **Updated** 2022-02-15. Added a notice explaining that the template hierarchy is the same for classic and block themes, but that the examples uses .php files and block themes use .html files.