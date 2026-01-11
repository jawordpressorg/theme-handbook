<!--
# Template Hierarchy
 -->

# テンプレート階層

<!--
As discussed, [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template files page") are modular, reusable files, used to generate the web pages on your WordPress site. Some template files (such as the header and footer template) are used on all of your site’s pages, while others are used only under specific conditions.
 -->

前述のとおり、[テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/ "Template files page") とは、あなたの WordPress サイトで Web ページを生成するために使用される、モジュール化された再利用可能なファイルです。(ヘッダーやフッター・テンプレートなど) 一部のテンプレート・ファイルは、あなたのサイト内の全ページで使用されますが、他のテンプレート・ファイルは、特定の条件下でのみ使用されます。

<!--
This article explains **how WordPress determines which template file(s) to use on individual pages**. If you want to customize an existing WordPress theme it will help you decide which template file needs to be edited.
 -->

本稿では、**WordPress が、個々のページでどのテンプレート・ファイルを使用するかを決定する方法** について説明します。既存の WordPress テーマをカスタマイズしたい場合、どのテンプレート・ファイルを編集すべきかを判断するのに役立ちます。

<!--
You can also use [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags") to control which templates are loaded on a specific page.
 -->

特定のページでロードするテンプレートを制御するには、[条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags") も使用できます。

<!--
## The Template File Hierarchy
 -->

## テンプレート・ファイル階層

<!--
### Overview
 -->

### 概要

<!--
WordPress uses the [query string](https://wordpress.org/support/article/glossary/#query-string) to decide which template or set of templates should be used to display the page. The query string is information that is contained in the link to each part of your website.
 -->

WordPress は、[クエリー文字列](https://wordpress.org/support/article/glossary/#query-string) を使用して、ページを表示するために、どのテンプレートまたはテンプレートのセットを使用すべきかを決定します。クエリー文字列とは、あなたの Web サイト内の各部分へのリンクに含まれる情報です。

<!--
Put simply, WordPress searches down through the template hierarchy until it finds a matching template file. To determine which template file to use, WordPress:
 -->

簡単に言えば、WordPress は、合致するテンプレート・ファイルが見つかるまで、テンプレート階層を下に向かって検索します。使用するテンプレート・ファイルを決定するために、WordPress は:

<!--
1.  Matches every query string to a query type to decide which page is being requested (for example, a search page, a category page, etc);
2.  Selects the template in the order determined by the template hierarchy;
3.  Looks for template files with specific names in the current theme’s directory and uses the **first matching template file** as specified by the hierarchy.
 -->

1.  クエリー文字列をクエリー・タイプに照合し、要求されているページ (たとえば、検索ページ、カテゴリー・ページなど) を決定します;
2.  テンプレート階層で決められた順序で、テンプレートを選択します;
3.  現在のテーマ・ディレクトリ内で、特定の名称を持つテンプレート・ファイルを検索し、階層構造で指定された **最初に合致したテンプレート・ファイル** を使用します。

<!--
With the exception of the basic `index.php` template file, you can choose whether you want to implement a particular template file or not.
 -->

基本の `index.php` テンプレート・ファイルを除き、特定のテンプレート・ファイルを実装するか否かを選択できます。

<!--
In these examples, the PHP file extension is used. In block themes, HTML files are used instead, but the template hierarchy is the same.
 -->

これらの例では、PHP ファイル拡張子が使用されています。ブロック・テーマでは、代わりに HTML ファイルが使用されますが、テンプレートの階層構造は同じです。

<!--
If WordPress cannot find a template file with a matching name, it will skip to the next file in the hierarchy. If WordPress cannot find any matching template file, the theme’s `index.php` file will be used.
 -->

WordPress が、合致する名称を持つテンプレート・ファイルを見つけられない場合、階層構造上の次のファイルにスキップします。WordPress が、合致するテンプレート・ファイルを一切見つけられない場合、テーマの `index.php` ファイルが使用されます。

<!--
When you are using a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/), any file you add to your child theme will over-ride the same file in the parent theme. For example, both themes contain the same template `category.php`, then child theme’s template is used.  
If a child theme contains the specific template such as `category-unicorns.php` and the parent theme contains lower prioritized template such as `category.php`, then child theme’s `category-unicorns.php` is used.  
Contrary, if a child theme contains general template only such as `category.php` and the parent theme contains the specific one such as `category-unicorns.php`, then parent’s template `category-unicorns.php` is used.
 -->

[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/) を使用している場合、あなたの子テーマに追加した任意のファイルは、親テーマ内の同じファイルをオーバーライドします。たとえば、両方のテーマに同じテンプレート `category.php` が含まれている場合、子テーマのテンプレートが使用されます。
子テーマに `category-unicorns.php` のような特定のテンプレートが含まれており、親テーマに `category.php` のような優先度の低いテンプレートが含まれている場合、子テーマの `category-unicorns.php` が使用されます。
逆に、子テーマに `category.php` のような一般的なテンプレートのみが含まれており、親テーマに `category-unicorns.php` のような特定のテンプレートが含まれている場合、親テーマのテンプレート `category-unicorns.php` が使用されます。

<!--
### Examples
 -->

### 例

<!--
If your blog is at `http://example.com/blog/` and a visitor clicks on a link to a category page such as `http://example.com/blog/category/your-cat/`, WordPress looks for a template file in the current theme’s directory that matches the category’s ID to generate the correct page. More specifically, WordPress follows this procedure:
 -->

あなたのブログが `http://example.com/blog/` にあり、訪問者が `http://example.com/blog/category/your-cat/` のようなカテゴリー・ページへのリンクをクリックした場合、WordPress は現在のテーマ・ディレクトリ内で、そのカテゴリーの ID に合致するテンプレート・ファイルを探し、正しいページを生成します。より具体的には、WordPress は、以下の手順に従います:

<!--
1.  Looks for a template file in the current theme’s directory that matches the category’s slug. If the category slug is “unicorns,” then WordPress looks for a template file named `category-unicorns.php`.
2.  If `category-unicorns.php` is missing and the category’s ID is 4, WordPress looks for a template file named `category-4.php`.
3.  If `category-4.php` is missing, WordPress will look for a generic category template file, `category.php`.
4.  If `category.php` does not exist, WordPress will look for a generic archive template, `archive.php`.
5.  If `archive.php` is also missing, WordPress will fall back to the main theme template file, `index.php`.
 -->

1.  現在のテーマ・ディレクトリ内で、カテゴリーのスラッグに合致するテンプレート・ファイルを検索します。カテゴリーのスラッグが「unicorns」の場合、WordPress は `category-unicorns.php` という名称のテンプレート・ファイルを探します。
2. `category-unicorns.php` が存在せず、カテゴリーの ID が4の場合、WordPress は `category-4.php` という名称のテンプレート・ファイルを探します。
3. `category-4.php` が存在しない場合、WordPress は汎用カテゴリー・テンプレート・ファイルである `category.php` を探します。
4. `category.php` が存在しない場合、WordPress は汎用アーカイブ・テンプレートである `archive.php` を探します。
5. `archive.php` も存在しない場合、WordPress はメイン・テーマ・テンプレート・ファイルである `index.php` にフォールバックします。

<!--
### Visual Overview
 -->

### 図解による概要

<!--
The following diagram shows which template files are called to generate a WordPress page based on the WordPress template hierarchy.
 -->

以下の図は、WordPress のテンプレート階層にもとづいて WordPress ページを生成する際にコールされる、テンプレート・ファイルを示しています。

<!-- 
[![](https://i0.wp.com/developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png?resize=1024%2C639&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png?ssl=1)
 -->

[![](https://i0.wp.com/developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png?resize=1024%2C639&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2014/10/Screenshot-2019-01-23-00.20.04.png?ssl=1)

<!--
## The Template Hierarchy In Detail
 -->

## テンプレート階層の詳細

<!--
While the template hierarchy is easier to understand as a diagram, the following sections describe the order in which template files are called by WordPress for a number of query types.
 -->

テンプレートの階層構造は図として理解しやすいですが、以下のセクションでは、WordPress が各種クエリー・タイプに対してテンプレート・ファイルをコールする、順序について説明します。

<!--
### Home Page display
 -->

### ホームページ表示

<!--
By default, WordPress sets your site’s home page to display your latest blog posts. This page is called the blog posts index. You can also set your blog posts to display on a separate static page. The template file `home.php` is used to render the blog posts index, whether it is being used as the front page or on separate static page. If `home.php` does not exist, WordPress will use `index.php`.
 -->

デフォルトでは、WordPress は、あなたのサイトのホームページに、あなたの最新のブログ投稿を表示するように設定されています。本ページは、ブログ投稿インデックスと称されます。あるいは、別の固定ページにあなたのブログ投稿を表示するようにも設定できます。テンプレート・ファイル `home.php` は、ブログ投稿インデックスをレンダリングするために使用され、フロントページとして使用される場合でも、別の固定ページとして使用される場合でも同様です。`home.php` が存在しない場合、WordPress は `index.php` を使用します。

<!-- 
1.  `home.php`
2.  `index.php`
 -->

1.  `home.php`
2.  `index.php`

<!--
If `front-page.php` exists, it will override the `home.php` template.
 -->

`front-page.php` が存在する場合、`home.php` テンプレートをオーバーライドします。

<!--
### Front Page display
 -->

### フロントページ表示

<!-- 
The `front-page.php` template file is used to render your site’s front page, whether the front page displays the blog posts index (mentioned above) or a static page. The front page template takes precedence over the blog posts index (`home.php`) template. If the `front-page.php` file does not exist, WordPress will either use the `home.php` or `page.php` files depending on the setup in Settings → Reading. If neither of those files exist, it will use the `index.php` file.
 -->

`front-page.php` テンプレート・ファイルは、あなたのサイトのフロントページをレンダリングするために使用されます。フロントページが (前述の) ブログ投稿インデックスを表示する場合でも、固定ページを表示する場合でも同様です。フロントページ・テンプレートは、ブログ投稿インデックス (`home.php`) テンプレートよりも優先されます。`front-page.php` ファイルが存在しない場合、WordPress は、「設定→表示設定」での設定に応じて、`home.php` または `page.php` ファイルを使用します。これらのファイルも存在しない場合、`index.php` ファイルが使用されます。

<!--
1.  `front-page.php` – Used for both “**your latest posts**” or “**a static page**” as set in the **front page displays** section of Settings → Reading.
2.  `home.php` – If WordPress cannot find `front-page.php` and “**your latest posts**” is set in the **front page displays** section, it will look for `home.php`. Additionally, WordPress will look for this file when the **posts page** is set in the **front page displays** section.
3.  `page.php` – When “**front page**” is set in the **front page displays** section.
4.  `index.php` – When “**your latest posts**” is set in the **front page displays** section but `home.php` does not exist *or* when **front page** is set but `page.php` does not exist.
 -->

1. `front-page.php` -「設定→表示設定」の「ホームページの表示」セクションで設定された、「**最新の投稿**」または「**固定ページ**」の両方に使用されます。
2. `home.php` - WordPress が `front-page.php` を見つけられず、**ホームページの表示** セクションで「**最新の投稿**」が設定されている場合、`home.php` を探します。さらに、**ホームページの表示** セクションで **投稿ページ** が設定されている場合にも、WordPress は、このファイルを探します。
3. `page.php` – **ホームページの表示** セクションで「**ホームページ**」が設定されている場合。
4. `index.php` – **ホームページの表示** セクションで「**最新の投稿**」が設定されているが、`home.php` が存在しない場合、*または*「**ホームページ**」が設定されているが、`page.php` が存在しない場合。

<!--
As you can see, there are a lot of rules to what path WordPress takes. Using the chart above is the best way to determine what WordPress will display.
 -->

ご覧の通り、WordPress がどのパスを取るかには、多くのルールが存在します。上記のチャートを使用することが、WordPress が何を表示するかを判断する、最良の方法です。

<!--
### Privacy Policy Page display
 -->

### プライバシー・ポリシー・ページ表示

<!--
The `privacy-policy.php` template file is used to render your site’s Privacy Policy page. The Privacy Policy page template takes precedence over the static page (`page.php`) template. If the `privacy-policy.php` file does not exist, WordPress will either use the `page.php` or `singular.php` files depending on the available templates. If neither of those files exist, it will use the `index.php` file.
 -->

`privacy-policy.php` テンプレート・ファイルは、あなたのサイトの「プライバシー・ポリシー」ページをレンダリングするために使用されます。「プライバシー・ポリシー」ページ・テンプレートは、固定ページ (`page.php`) テンプレートよりも優先されます。`privacy-policy.php` ファイルが存在しない場合、WordPress は利用可能なテンプレートに応じて、`page.php` または `singular.php` ファイルを使用します。これらのファイルも存在しない場合、`index.php` ファイルが使用されます。

<!--
1.  `privacy-policy.php` – Used for the Privacy Policy page set in the **Change your Privacy Policy page** section of Settings → Privacy.
2.  `custom template file` – The [page template](https://developer.wordpress.org/themes/template-files-section/page-template-files/) assigned to the page. See `get_page_templates()`.
3.  `page-{slug}.php` – If the page slug is `privacy`, WordPress will look to use `page-privacy.php`.
4.  `page-{id}.php` – If the page ID is 6, WordPress will look to use `page-6.php`.
5.  `page.php`
6.  `singular.php`
7.  `index.php`
 -->

1.  `privacy-policy.php` –「設定→プライバシー」の **プライバシー・ポリシー・ページを選択** セクションで設定された、「プライバシー・ポリシー」ページに使用されます。
2.  `カスタム・テンプレート・ファイル` – ページに割り当てられた [ページ・テンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/) です。`get_page_templates()` をご覧ください。
3.  `page-{slug}.php` – ページ・スラッグが `privacy` の場合、WordPress は `page-privacy.php` を使用しようとします。
4.  `page-{id}.php` – ページ ID が6の場合、WordPress は `page-6.php` を使用しようとします。
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

個別投稿テンプレート・ファイルは、単一の投稿をレンダリングするために使用されます。WordPress は以下のパスを使用します:

<!--
1.  `single-{post-type}-{slug}.php` – (Since 4.4) First, WordPress looks for a template for the specific post. For example, if [post type](https://developer.wordpress.org/themes/basics/post-types/) is `product` and the post slug is `dmc-12`, WordPress would look for `single-product-dmc-12.php`.
2.  `single-{post-type}.php` – If the post type is `product`, WordPress would look for `single-product.php`.
3.  `single.php` – WordPress then falls back to `single.php`.
4.  `singular.php` – Then it falls back to `singular.php`.
5.  `index.php` – Finally, as mentioned above, WordPress ultimately falls back to `index.php`.
 -->

1.  `single-{post-type}-{slug}.php` - (v4.4以降) まず WordPress は特定の投稿用のテンプレートを探します。たとえば、[投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/) が `product` で投稿スラッグが `dmc-12` の場合、WordPress は `single-product-dmc-12.php` を探します。
2.  `single-{post-type}.php` - 投稿タイプが `product` の場合、WordPress は `single-product.php` を探します。
3.  `single.php` - 次に、WordPress は `single.php` にフォールバックします。
4.  `singular.php` - その後、`singular.php` にフォールバックします。
5.  `index.php` - 最後に、前述の通り、WordPress は最終的に `index.php` にフォールバックします。

<!--
### Single Page
 -->

### 個別ページ

<!--
The template file used to render a static page (`page` post-type). Note that unlike other post-types, `page` is special to WordPress and uses the following path:
 -->

固定ページ (`page` 投稿タイプ) をレンダリングするために使用されるテンプレート・ファイルです。他の投稿タイプとは異なり、`page` は WordPress 独自の投稿タイプであり、以下のパスを使用することに注意してください:

<!--
1.  `custom template file` – The [page template](https://developer.wordpress.org/themes/template-files-section/page-template-files/) assigned to the page. See `[get_page_templates()](https://developer.wordpress.org/reference/functions/get_page_templates/)`.
2.  `page-{slug}.php` – If the page slug is `recent-news`, WordPress will look to use `page-recent-news.php`.
3.  `page-{id}.php` – If the page ID is 6, WordPress will look to use `page-6.php`.
4.  `page.php`
5.  `singular.php`
6.  `index.php`
 -->

1.  `カスタム・テンプレート・ファイル` - ページに割り当てられた [ページ・テンプレート](https://developer.wordpress.org/themes/template-files-section/page-template-files/) です。`[get_page_templates()](https://developer.wordpress.org/reference/functions/get_page_templates/)` をご覧ください。
2.  `page-{slug}.php` - ページのスラッグが `recent-news` の場合、WordPress は `page-recent-news.php` を使用しようとします。
3.  `page-{id}.php` - ページ ID が6の場合、WordPress は `page-6.php` を使用しようとします。
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

WordPress では、カテゴリー・アーカイブ・インデックス・ページをレンダリングする際に、以下のパスを使用します:

<!--
1.  `category-{slug}.php` – If the category’s slug is `news`, WordPress will look for `category-news.php`.
2.  `category-{id}.php` – If the category’s ID is `6`, WordPress will look for `category-6.php`.
3.  `category.php`
4.  `archive.php`
5.  `index.php`
 -->

1.  `category-{slug}.php` - カテゴリーのスラッグが `news` の場合、WordPress は `category-news.php` を探します。
2.  `category-{id}.php` - カテゴリーの ID が6の場合、WordPress は `category-6.php` を探します。
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

タグ・アーカイブ・インデックス・ページをレンダリングするために、WordPress は以下のパスを使用します:

<!--
1.  `tag-{slug}.php` – If the tag’s slug is `sometag`, WordPress will look for `tag-sometag.php`.
2.  `tag-{id}.php` – If the tag’s ID is `6`, WordPress will look for `tag-6.php`.
3.  `tag.php`
4.  `archive.php`
5.  `index.php`
 -->
1.  `tag-{slug}.php` - タグのスラッグが `sometag` の場合、WordPress は `tag-sometag.php` を探します。
2.  `tag-{id}.php` - タグの ID が6の場合、WordPress は `tag-6.php` を探します。
3.  `tag.php`
4.  `archive.php`
5.  `index.php`

<!--
### Custom Taxonomies
 -->

### カスタム・タクソノミー

<!--
[Custom taxonomies](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) use a slightly different template file path:
 -->

[カスタム・タクソノミー](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) では、テンプレート・ファイルのパスが若干異なります:

<!--
1.  `taxonomy-{taxonomy}-{term}.php` – If the taxonomy is `sometax`, and taxonomy’s term is `someterm`, WordPress will look for `taxonomy-sometax-someterm.php.` In the case of [post formats](https://developer.wordpress.org/themes/functionality/post-formats/), the taxonomy is ‘post\_format’ and the terms are ‘post-format-{format}. i.e. `taxonomy-post_format-post-format-link.php` for the link post format.
2.  `taxonomy-{taxonomy}.php` – If the taxonomy were `sometax`, WordPress would look for `taxonomy-sometax.php`.
3.  `taxonomy.php`
4.  `archive.php`
5.  `index.php`
 -->

1.  `taxonomy-{taxonomy}-{term}.php` - タクソノミーが `sometax` で、タクソノミーのタームが `someterm` の場合、WordPress は `taxonomy-sometax-someterm.php` を探します。[投稿フォーマット](https://developer.wordpress.org/themes/functionality/post-formats/) の場合、タクソノミーは `post_format` で、タームは `post-format-{format}` です。たとえば、リンク投稿フォーマットの場合、`taxonomy-post_format-post-format-link.php` になります。
2.  `taxonomy-{taxonomy}.php` - タクソノミーが `sometax` の場合、WordPress は `taxonomy-sometax.php` を探します。
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

[カスタム投稿タイプ](https://developer.wordpress.org/themes/basics/post-types/) は、適切なアーカイブ・インデックス・ページをレンダリングするために、以下のパスを使用します。

<!--
1.  `archive-{post_type}.php` – If the post type is `product`, WordPress will look for `archive-product.php`.
2.  `archive.php`
3.  `index.php`
 -->
1. `archive-{post_type}.php` - 投稿タイプが `product` の場合、WordPress は `archive-product.php` を探します。
2.  `archive.php`
3.  `index.php`

<!--
(For rendering a single post type template, refer to the [single post display](#single-post "Single Post Display") section above.)
 -->

(個別投稿タイプ・テンプレートのレンダリングについては、上記の [個別投稿の表示](#single-post "Single Post Display") セクションを参照してください)

<!--
### Author display
 -->

### 投稿者表示

<!--
Based on the above examples, rendering author archive index pages is fairly explanatory:
 -->

上記の例にもとづけば、投稿者アーカイブ・インデックス・ページのレンダリングは、かなり自明です:

<!--
1.  `author-{nicename}.php` – If the author’s nice name is `matt`, WordPress will look for `author-matt.php`.
2.  `author-{id}.php` – If the author’s ID were `6`, WordPress will look for `author-6.php`.
3.  `author.php`
4.  `archive.php`
5.  `index.php`
 -->
1.  `author-{nicename}.php` - 投稿者のニックネームが `matt` の場合、WordPress は `author-matt.php` を探します。
2.  `author-{id}.php` - 作者の ID が6の場合、WordPress は `author-6.php` を探します。
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

日付ベースのアーカイブ・インデックス・ページは、予想通りレンダリングされます:

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

検索結果は、他のテンプレート・タイプと同様のパターンに従います:

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

同様に、404テンプレート・ファイルは、この順序でコールされます:

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

添付ファイルページ (`attachment` 投稿タイプ) のレンダリングは、以下のパスを使用します:

<!--
1.  `{MIME-type}.php` – can be any [MIME type](http://en.wikipedia.org/wiki/Internet_media_type "http://en.wikipedia.org/wiki/Internet_media_type") (For example: `image.php`, `video.php`, `pdf.php`). For `text/plain`, the following path is used (in order):
    1.  `text-plain.php`
    2.  `plain.php`
    3.  `text.php`
2.  `attachment.php`
3.  `single-attachment-{slug}.php` – For example, if the attachment slug is `holiday`, WordPress would look for `single-attachment-holiday.php`.
4.  `single-attachment.php`
5.  `single.php`
6.  `singular.php`
7.  `index.php`
 -->

1.  `{MIME-type}.php` - 任意の [MIME タイプ](http://en.wikipedia.org/wiki/Internet_media_type "http://en.wikipedia.org/wiki/Internet_media_type") が使用可能です (たとえば `image.php`、`video.php`、`pdf.php`)。`text/plain` の場合、(順に) 以下のパスが使用されます:
    1.  `text-plain.php`
    2.  `plain.php`
    3.  `text.php`
2.  `attachment.php`
3.  `single-attachment-{slug}.php` - たとえば、添付ファイルのスラッグが `holiday` の場合、WordPress は `single-attachment-holiday.php` を探します。
4.  `single-attachment.php`
5.  `single.php`
6.  `singular.php`
7.  `index.php`

<!-- 
As of WordPress 6.4, attachment pages are [no longer enabled by default](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/) on new installations. Users can enable them with a plugin, so it is still good practice to test your theme and ensure it properly displays content when viewing an attachment page.
 -->

WordPress v6.4以降、新規インストール時において、添付ファイル・ページは、[デフォルトでは、有効化されなくなりました](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/)。ユーザーはプラグインで有効化できるため、添付ファイル・ページを表示した際にコンテンツが正しく表示されるよう、あなたのテーマをテストすることは、依然としてグッド・プラクティスです。

<!--
### Embeds
 -->

### 埋め込み

<!--
The embed template file is used to render a post which is being embedded. Since 4.5, WordPress uses the following path:
 -->

埋め込みテンプレート・ファイルは、埋め込まれている投稿をレンダリングするために使用されます。v4.5以降、WordPress は以下のパスを使用します:

<!--
1.  `embed-{post-type}-{post_format}.php` – First, WordPress looks for a template for the specific post. For example, if its post type is `post` and it has the audio format, WordPress would look for `embed-post-audio.php`.
2.  `embed-{post-type}.php` – If the post type is `product`, WordPress would look for `embed-product.php`.
3.  `embed.php` – WordPress then falls back to embed`.php`.
4.  Finally, WordPress ultimately falls back to its own `wp-includes/theme-compat/embed.php` template.
 -->

1.  `embed-{post-type}-{post_format}.php` - まず、WordPress は特定の投稿用のテンプレートを探します。たとえば、投稿タイプが `post` で音声フォーマットの場合、WordPress は `embed-post-audio.php` を探します。
2.  `embed-{post-type}.php` - 投稿タイプが `product` の場合、WordPress は `embed-product.php` を探します。
3.  `embed.php` - 次に WordPress は `embed.php` にフォールバックします。
4.  最終的に、WordPress は自身の `wp-includes/theme-compat/embed.php` テンプレートにフォールバックします。

<!--
## Non-ASCII Character Handling
 -->

## 非 ASCII 文字の取り扱い

<!--
Since WordPress 4.7, any dynamic part of a template name which includes non-ASCII characters in its name actually supports both the un-encoded and the encoded form, in that order. You can choose which to use.
 -->

WordPress v4.7以降、テンプレート名に含まれる動的部分で、非 ASCII 文字を含むものは、エンコードされていない形式とエンコードされた形式の両方を、実際にはその順序でサポートしています。どちらを使用するか選択できます。

<!--
Here’s the page template hierarchy for a page named “Hello World 😀” with an ID of `6`:
 -->

ID が6の「Hello World 😀」という名称の、ページ用のページ・テンプレート階層は、以下の通りです:

<!-- 
*   `page-hello-world-😀.php`
*   `page-hello-world-%f0%9f%98%80.php`
*   `page-6.php`
*   `page.php`
*   `singular.php`
 -->

*   `page-hello-world-😀.php`
*   `page-hello-world-%f0%9f%98%80.php`
*   `page-6.php`
*   `page.php`
*   `singular.php`

<!--
The same behaviour applies to post slugs, term names, and author nicenames.
 -->

同じ挙動は、投稿スラッグ、ターム名称、および作者ニックネームにも適用されます。

<!--
## Filter Hierarchy
 -->

## フィルター階層

<!--
The WordPress template system lets you filter the hierarchy. This means that you can insert and change things at specific points of the hierarchy. The filter (located in the [`get_query_template()`](https://developer.wordpress.org/reference/functions/get_query_template/) function) uses this filter name: `"{$type}_template"` where `$type` is the template type.
 -->

WordPress のテンプレート・システムでは、階層構造をフィルタリングできます。つまり、階層構造の特定のポイントで、要素を挿入したり変更したりできます。([`get_query_template()`](https://developer.wordpress.org/reference/functions/get_query_template/) 関数内に存在する) フィルターは、次のフィルター名を使用します: `"{$type}_template"` (ここで `$type` はテンプレート・タイプを指す)。

<!--
Here is a list of all available filters in the template hierarchy:
 -->

テンプレート階層で利用可能な、すべてのフィルターのリストは、以下の通りです:

<!-- 
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
 -->

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
For example, let ’s take the default author hierarchy:
 -->

たとえば、デフォルトの作者階層を例に取ると:

<!-- 
*   `author-{nicename}.php`
*   `author-{id}.php`
*   `author.php`
 -->

*   `author-{nicename}.php`
*   `author-{id}.php`
*   `author.php`

<!--
To add `author-{role}.php` before `author.php`, we can manipulate the actual hierarchy using the ‘author\_template’ template type. This allows a request for /author/username where username has the role of editor to display using author-editor.php if present in the current themes directory.
 -->

`author.php` の前に `author-{role}.php` を追加するには、`author_template` テンプレート・タイプを使用して、実際の階層を操作できます。これにより、`/author/username` へのリクエストにおいて、`username` が編集者権限を持つ場合、現在のテーマ・ディレクトリに `author-editor.php` が存在すれば、それを使用して表示できます。

```php
function author_role_template( $templates = '' ) {
	$author = get_queried_object();
	$role   = $author->roles[0];

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

<!--
Changelog:
 -->

変更履歴:

<!--
*   **Updated** 2022-02-15. Added a notice explaining that the template hierarchy is the same for classic and block themes, but that the examples uses .php files and block themes use .html files.
 -->
*   **更新** 2022-02-15。クラシック・テーマとブロック・テーマでは、テンプレート階層は同じだが、クラシック・テーマの例では `.php` ファイルを使用しているのに対し、ブロック・テーマの例では `.html` ファイルを使用している旨を説明する、注記を付加しました。