<!-- 
# Page Templates
 -->

# ページ・テンプレート

<!-- 
Page templates are a specific type of [template file](https://developer.wordpress.org/themes/basics/template-files/ "Template Files") that can be applied to a specific page or groups of pages.
 -->

ページ・テンプレートは、特定のページまたはページ群に適用できる [テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/ "Template Files") の一種です。

<!-- 
As of WordPress 4.7 page templates support all post types. For more details how to set a page template to specific post types [see example below](#creating-page-templates-for-specific-post-types).
 -->

WordPress v4.7以降、ページ・テンプレートは、すべての投稿タイプをサポートしています。特定の投稿タイプにページ・テンプレートを設定する方法の詳細については、[以下の例をご覧ください](#creating-page-templates-for-specific-post-types)。

<!-- 
Since a page template is a specific type of template file, here are some distinguishing features of page templates:
 -->

ページ・テンプレートはテンプレート・ファイルの一種であるため、以下にページ・テンプレートの特徴を挙げます:

<!-- 
*   Page templates are used to change the look and feel of a page.
*   A page template can be applied to a single page, a page section, or a class of pages.
*   Page templates generally have a high level of specificity, targeting an individual page or group of pages. For example, a page template named `page-about.php` is more specific than the template files `page.php` or `index.php` as it will only affect a page with the slug of “about.”
*   If a page template has a template name, WordPress users editing the page have control over what template will be used to render the page.
 -->

*   ページ・テンプレートは、ページのルック＆フィールを変化させるために使用されます。
*   ページ・テンプレートは、個別のページ、ページ・セクション、またはページ群のクラスに適用できます。
*   ページ・テンプレートは一般的に高い特異性を持っており、単独のページまたはページ群を対象とします。たとえば、`page-about.php` というページ・テンプレートは、`page.php` や `index.php` といったテンプレート・ファイルよりも特異性が高く、「about」というスラッグを持つページにのみ影響します。
*   ページ・テンプレートにテンプレート名がある場合、WordPress ユーザーは、ページ編集時に、ページをレンダリングするために使用するテンプレートを制御できます。

<!-- 
## Uses for Page Templates
 -->

## ページ・テンプレートの用途

<!-- 
Page templates display your site’s dynamic content on a page, e.g., posts, news updates, calendar events, media files, etc. You may decide that you want your homepage to look a specific way, that is quite different to other parts of your site. Or, you may want to display a featured image that links to a post on one part of the page, have a list of latest posts elsewhere, and use a custom navigation. You can use page templates to achieve these things.
 -->

ページ・テンプレートは、投稿、ニュース更新、カレンダー・イベント、メディア・ファイルなど、あなたのサイトにおける動的コンテンツを、ページ上に表示します。あなたのホームページを、あなたのサイト内の他の部分とはかなり異なる、特定の見た目にしたいと考えるかもしれません。あるいは、ページの一部に投稿にリンクするアイキャッチ画像を表示したり、別の場所に最新投稿のリストを表示したり、カスタム・ナビゲーションを使用したりしたいかもしれません。ページ・テンプレートを使用することで、こうしたことを実現できます。

<!-- 
This section shows you how to build page templates that can be selected by your users through their admin screens.
 -->

本セクションでは、ユーザーが管理画面から選択できる、ページ・テンプレートの作成方法を説明します。

<!-- 
For example, you can build page templates for:
 -->

たとえば、次のようなページ・テンプレートを作成できます:

<!-- 
*   full-width, one-column
*   two-column with a sidebar on the right
*   two-column with a sidebar on the left
*   three-column
 -->

*   全幅で、1カラム
*   右側にサイドバーがある、2カラム
*   左側にサイドバーがある、2カラム
*   3カラム

<!-- 
## Page Templates within the Template Hierarchy
 -->

## テンプレート階層内のページ・テンプレート

<!-- 
When a person browses to your website, WordPress selects which template to use for rendering that page. As we learned earlier in the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy"), WordPress looks for template files in the following order:
 -->

ユーザーがあなたの Web サイトを閲覧すると、WordPress は、そのページをレンダリングするために使用するテンプレートを、選択します。[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") で学んだように、WordPress は、次の順序でテンプレート・ファイルを検索します:

<!-- 
1.  **Page Template —** If the page has a custom template assigned, WordPress looks for that file and, if found, uses it.
2.  **`page-{slug}.php` —** If no custom template has been assigned, WordPress looks for and uses a specialized template that contains the page’s slug.
3.  **`page-{id}.php` —** If a specialized template that includes the page’s slug is not found, WordPress looks for and uses a specialized template named with the page’s ID.
4.  **`page.php` —** If a specialized template that includes the page’s ID is not found, WordPress looks for and uses the theme’s default page template.
5.  **`singular.php` —** If `page.php` is not found, WordPress looks for and uses the theme’s template used for a single post, irregardless of post type.
6.  **`index.php` —** If no specific page templates are assigned or found, WordPress defaults back to using the theme’s index file to render pages.
 -->

1.  **ページ・テンプレート** — ページにカスタム・テンプレートが割り当てられている場合、WordPress は、そのファイルを検索し、見つかった場合はそれを使用します。
2.  **`page-{slug}.php`** — カスタム・テンプレートが割り当てられていない場合、WordPress は、ページのスラッグを含む専用テンプレートを検索し、使用します。
3.  **`page-{id}.php`** — ページのスラッグを含む専用テンプレートが見つからない場合、WordPress は、ページ ID で命名された専用テンプレートを検索し、使用します。
4.  **`page.php`** — ページ ID を含む専用テンプレートが見つからない場合、WordPress は、テーマのデフォルト・ページ・テンプレートを検索し、使用します。
5.  **`singular.php`** — `page.php` が見つからない場合、WordPress は、投稿タイプに関係なく、個別投稿用に使用されるテーマのテンプレートを検索し、使用します。
6.  **`index.php`** — 特定のページ・テンプレートが割り当てられていない、または見つからない場合、WordPress は、デフォルトでテーマの index ファイルを使用して、ページをレンダリングします。

<!-- 
There is also a WordPress-defined template named `paged.php`. It is *not* used for the page post-type but rather for displaying multiple pages of archives.
 -->

WordPress で定義された `paged.php` というテンプレートも存在します。これは投稿タイプ「ページ」には使用 *されず*、複数のアーカイブ・ページを表示するために、使用されます。

<!-- 
## Page Templates Purpose & User Control
 -->

## ページ・テンプレートの目的とユーザー・コントロール

<!-- 
If you plan on making a custom page template for your theme, you should decide a couple of things before proceeding:
 -->

あなたのテーマ用にカスタム・ページ・テンプレートを作成する予定なら、作業を進める前に、以下の点を事前に決定しておくべきです:

<!-- 
*   Whether the page template will be for one specific page or for any page; and
*   What type of user control you want available for the template.
 -->

*   ページ・テンプレートが特定の1ページ専用か、任意のページで使用可能か; および
*   テンプレートで使用可能にしたい、ユーザー・コントロールの種類。

<!-- 
Every page template that has a template name can be selected by a user when they create or edit a page. The list of available templates can be found at **Pages > Add New > Attributes > Template**. Therefore, a WordPress user can choose any page template with a template name, which might not be your intention.
 -->

ページを作成または編集する際、テンプレート名を持つすべてのページ・テンプレートが、ユーザーによって選択できます。利用可能なテンプレートのリストは、**ページ > 新規追加 > 属性 > テンプレート** で確認できます。したがって、WordPress ユーザーは、あなたの意図とは異なる可能性のある、テンプレート名を持つ任意のページ・テンプレートを選択できます。

<!-- 
For example, if you want to have a specific template for your “About” page, it might not be appropriate to name that page template “About Template” as it would be globally available to all pages (i.e. the user could apply it to any page). Instead, [create a single use template](https://developer.wordpress.org/themes/template-files-section/page-template-files/#creating-a-custom-page-template-for-one-specific-page) and WordPress will render the page with the appropriate template, whenever a user visits the “About” page.
 -->

たとえば、あなたの「About」ページ用に特定のテンプレートを用意したい場合、そのページ・テンプレートを「About Template」と命名するのは、適切ではないかもしれません。なぜなら、そのテンプレートは全ページでグローバルに利用可能になってしまうからです (たとえば、ユーザーが任意のページに適用できてしまう)。代わりに、[単一用途のテンプレートを作成](https://developer.wordpress.org/themes/template-files-section/page-template-files/#creating-a-custom-page-template-for-one-specific-page) すると、ユーザーが「About」ページにアクセスするたびに、WordPress は、適切なテンプレートでページをレンダリングします。

<!-- 
Conversely, many themes include the ability to choose how many columns a page will have. Each of these options is a page template that is available globally. To give your WordPress users this global option, you will need to create page templates for each option and give each a template name.
 -->

逆に、多くのテーマでは、ページに表示するカラム数を設定する機能を備えています。これらの各オプションは、グローバルに利用可能なページ・テンプレートです。あなたの WordPress ユーザーに、このグローバル・オプションを提供するためには、各オプションに対応するページ・テンプレートを作成し、それぞれにテンプレート名を設定する必要があります。

<!-- 
Dictating whether a template is for global use vs. singular use is achieved by the way the file is named and whether or not is has a specific comment.
 -->

テンプレートがグローバル使用か個別使用かを決定する方法は、ファイル名の付け方と特定のコメントの有無によって実現されます。

<!-- 
Sometimes it is appropriate to have a template globally available even if it appears to be a single use case. When you’re creating themes for release, it can be hard to predict what a user will name their pages. Portfolio pages are a great example as not every WordPress user will name their portfolio the same thing or have the same page ID and yet they may want to use that template.
 -->

単一のユース・ケースにしか見えない場合でも、テンプレートをグローバルに利用可能にしておくことが、適切な場合があります。リリース用のテーマを作成する際、ユーザーがそれぞれのページにどのような名前を付けるかを予測するのは困難です。ポートフォリオ・ページはその好例で、すべての WordPress ユーザーがポートフォリオに同じ名前を付けたり、同じページ ID を持つわけではありませんが、それでもそのテンプレートを使用したい場合があるからです。

<!-- 
## File Organization of Page Templates
 -->

## ページ・テンプレートのファイル構成

<!-- 
As discussed in [Organizing Theme Files](https://developer.wordpress.org/themes/basics/organizing-theme-files/), WordPress recognizes the subfolder **page-templates**. Therefore, it’s a good idea to store your global page templates in this folder to help keep them organized.
 -->

[テーマ・ファイルの構成](https://developer.wordpress.org/themes/basics/organizing-theme-files/) で説明したように、WordPress は、**page-templates** サブ・フォルダーを認識します。したがって、あなたのグローバル・ページ・テンプレートをこのフォルダーに保存すると、構成しやすくなります。

<!-- 
A specialized page template file (those created for only one time use) **cannot** be in a sub-folder, nor, if using a [Child Theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/#how-to-create-a-child-theme), in the Parent Theme’s folder.
 -->

(1回限りの使用のために作成された) 専用ページ・テンプレート・ファイルは、サブ・フォルダー内に配置 **できません** し、また、[子テーマ](https://developer.wordpress.org/themes/advanced-topics/child-themes/#how-to-create-a-child-theme) を使用している場合、親テーマのフォルダー内にも配置できません。

<!-- 
## Creating Custom Page Templates for Global Use
 -->

## グローバル利用向けの、カスタム・ページ・テンプレートの作成

<!-- 
Sometimes you’ll want a template that can be used globally by any page, or by multiple pages.  Some developers will group their templates with a filename prefix, such as `page_two-columns.php`
 -->

時には、任意のページや複数のページで、グローバルに使用できるテンプレートが必要になる場合があります。一部の開発者は、`page_two-columns.php` のようにファイル名に接頭辞を付けて、テンプレートをグループ化します。

<!-- 
***Important!*** Do not use `page-` as a prefix, as WordPress will interpret the file as a specialized template, meant to apply to only *one* page on your site.
 -->

***重要 !*** WordPress は、このファイルを、あなたのサイト上の *1つのページ* だけに適用される特殊なテンプレートとして解釈してしまうため、`page-` を接頭辞として使用しないでください。

<!-- 
For information on theme file-naming conventions and filenames you cannot use, see [reserved theme filenames](https://developer.wordpress.org/themes/basics/template-files/#common-wordpress-template-files "Theme Development").
 -->

テーマ・ファイルの命名規則および使用できないファイル名については、[予約済みテーマ・ファイル名](https://developer.wordpress.org/themes/basics/template-files/#common-wordpress-template-files "Theme Development") をご覧ください。

<!-- 
A quick, safe method for creating a new page template is to make a copy of `page.php` and give the new file a distinct filename. That way, you start off with the HTML structure of your other pages and you can edit the new file as needed.
 -->

新規ページ・テンプレートをすばやく安全に作成する方法は、`page.php` をコピーし、新規ファイルに対して、区別可能なファイル名を付けることです。これにより、あなたの他のページの HTML 構造をもとに開始し、必要に応じて新規ファイルを編集できます。

<!-- 
To create a global template, write an opening PHP comment at the top of the file that states the template’s name.
 -->

グローバル・テンプレートを作成するには、ファイルの先頭にテンプレートの名称を明記した、PHP コメントを記述します。

```php
<?php /* Template Name: Example Template */ ?>
```

<!-- 
It’s a good idea to choose a name that describes what the template does as the name is visible to WordPress users when they are editing the page. For example, you could name your template Homepage, Blog, or Portfolio.
 -->

テンプレートの名前は、WordPress ユーザーがページを編集する際に表示されるため、その機能を表す名前を選ぶのが良いでしょう。たとえば、あなたのテンプレートを  Homepage、Blog、Portfolio などと名付けることができます。

<!-- 
This example from the TwentyFourteen theme creates a page template called Full Width Page:
 -->

「Twenty Fourteen」テーマにおける本例は、「Full Width Page」というページ・テンプレートを作成します:

```php
<?php
/**
* Template Name: Full Width Page
*
* @package WordPress
* @subpackage Twenty_Fourteen
* @since Twenty Fourteen 1.0
*/
```

<!-- 
![basics-page-templates-03](https://i0.wp.com/developer.wordpress.org/files/2014/10/basics-page-templates-03.png?resize=180%2C212&ssl=1)
 -->

![basics-page-templates-03](https://i0.wp.com/developer.wordpress.org/files/2014/10/basics-page-templates-03.png?resize=180%2C212&ssl=1)

<!-- 
Once you upload the file to your theme’s folder (e.g., page-templates), go to the **Page > Edit** screen in your admin dashboard.
 -->

ファイルをあなたのテーマのフォルダー (例: `page-templates`) にアップロードしたら、あなたの管理ダッシュボードの **ページ > 編集** 画面に移動してください。

<!-- 
On the right hand side under **attributes** you’ll see **template**.  This is where users are able to access your global page templates.
 -->

右側の **属性** の下に、**テンプレート** が表示されます。ここでユーザーはあなたのグローバル・ページ・テンプレートにアクセスできます。

<!-- 
The select list has a maximum width of 250px, so longer names may be cut off.
 -->

選択リストの最大幅は250px ですので、長い名前は途中で切られる可能性があります。

<!-- 
## Creating a Custom Page Template for One Specific Page
 -->

## 特定の1ページ向けの、カスタム・ページ・テンプレートの作成

<!-- 
As mentioned in the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") page, you can create a template for a specific page.  To create a template for one specific page, copy your existing `page.php` file and rename it with your page’s slug or ID:
 -->

[テンプレート階層](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") ページで述べたように、特定のページ用のテンプレートを作成できます。特定ページ用のテンプレートを作成するには、既存の `page.php` ファイルをコピーし、あなたのページのスラッグまたは ID で名称を変更します:

<!-- 
1.  `page-{slug}.php`
2.  `page-{ID}.php`
 -->

1.  `page-{slug}.php`
2.  `page-{ID}.php`

<!-- 
For example: Your About page has a slug of ‘about’ and an ID of 6. If your active theme’s folder has a file named `page-about.php` or `page-6.php`, then WordPress will automatically find and use that file to render the About page.
 -->

たとえば: あなたの「About」ページのスラッグは「about」、ID は6です。有効化されたテーマのフォルダー内に `page-about.php` または `page-6.php` というファイルが存在する場合、WordPress は、自動的にそのファイルを見つけて「About」ページをレンダリングします。

<!-- 
To be used, specialized page templates must be in your theme’s folder (i.e. **/wp-content/themes/my-theme-name/** ).
 -->

使用するには、専用ページ・テンプレートは、あなたのテーマ・フォルダー内 (例: **/wp-content/themes/my-theme-name/** ) に配置する必要があります。

<!-- 
## Creating page templates for specific post types
 -->

## 特定の投稿タイプ向けの、ページ・テンプレートの作成

<!-- 
By default, a custom page template will be available to the “page” post type.
 -->

デフォルトでは、カスタム・ページ・テンプレートは、投稿タイプ「ページ」で使用可能になります。

<!-- 
To create a page template to specific post types, add a line under the template name with the post types you would like the template to support.
 -->

特定の投稿タイプに適用するページ・テンプレートを作成するには、テンプレート名称の下に、そのテンプレートでサポートしたい投稿タイプを記述しましょう。

<!-- 
Example:
 -->

例:

```php
<?php
/*
Template Name: Full-width layout
Template Post Type: post, page, event
*/
// Page code here...
```

<!-- 
This ability to add page templates to post types other than “page” post type is supported only from WordPress 4.7
 -->

投稿タイプ「ページ」以外の投稿タイプにページ・テンプレートを追加するこの機能は、WordPress v4.7以降でのみサポートされています。

<!-- 
When at least one template exists for a post type, the ‘Post Attributes’ meta box will be displayed in the back end, without the need to add post type support for ‘page-attributes’ or anything else. The ‘Post Attributes’ label can be customzied per post type using the ‘attributes’ label when registering a post type.
 -->

投稿タイプに少なくとも1つのテンプレートが存在する場合、`page-attributes` やその他の投稿タイプ・サポートを追加する必要なく、管理画面に「投稿属性」メタボックスが表示されます。投稿タイプ登録時に `attributes` ラベルを使用することで、投稿タイプごとに「投稿属性」ラベルをカスタマイズできます。

<!-- 
**Backward Compatibility:**
 -->

**後方互換性:**

<!-- 
Let’s say you want to publicly release a theme with support for post type templates. WordPress versions before 4.7 will ignore the Template Post Type header and show the template in the list of page templates, even though it only works for regular posts. To prevent that, you can hook into the theme\_page\_templates filter to exclude it from the list. Here’s an example:
 -->

投稿タイプ・テンプレートをサポートするテーマを、公開リリースしたい場合を考えてみましょう。WordPress v4.7以前のバージョンでは、`Template Post Type` ヘッダーを無視し、通常の投稿でのみ機能するにもかかわらず、ページ・テンプレートのリストに表示してしまいます。このような事態を避けるには、`theme_page_templates` フィルターにフックして、リストから除外します。以下に例を示します:

```php
/**
 * Hides the custom post template for pages on WordPress 4.6 and older
 *
 * @param array $post_templates Array of page templates. Keys are filenames, values are translated names.
 * @return array Filtered array of page templates.
 */
function makewp_exclude_page_templates( $post_templates ) {
	if ( version_compare( $GLOBALS['wp_version'], '4.7', '&lt;' ) ) {
		unset( $post_templates['templates/my-full-width-post-template.php'] );
	}
	return $post_templates;
}

add_filter( 'theme_page_templates', 'makewp_exclude_page_templates' );
```

<!-- 
That way you can support custom post type templates in WordPress 4.7 and beyond while maintaining full backward compatibility.
 -->

これにより、WordPress v4.7以降のカスタム投稿タイプ・テンプレートをサポートしつつ、完全な下位互換性を維持できます。

<!-- 
Note that theme\_page\_templates is actually a dynamic theme\_{$post\_type}\_templates filter. The dynamic portion of the hook name, $post\_type, refers to the post type supported by the templates. E.g. you can hook into theme\_product\_templates to filter the list of templates for the product post type.
 -->

`theme_page_templates` は、実際には、動的な `theme_{$post_type}_templates` フィルターであることに注意してください。フック名の動的部分である `$post_type` は、テンプレートがサポートする投稿タイプを指します。たとえば、`theme_product_templates` にフックすることで、投稿タイプ `product` のテンプレート一覧をフィルタリングできます。

<!-- 
## Using Conditional Tags in Page Templates
 -->

## ページ・テンプレートでの、条件付きタグの使用

<!-- 
You can make smaller, page-specific changes with [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/) in your theme’s `page.php` file. For instance, the below example code loads the file `header-home.php` for your front page, but loads another file (`header-about.php`) for your About page, and then applies the default `header.php` for all other pages.
 -->

あなたのテーマの `page.php` ファイルで [条件付きタグ](https://developer.wordpress.org/themes/basics/conditional-tags/) を使用すると、ページごとに細かい変更を加えることができます。たとえば、以下のサンプル・コードでは、ホームページには `header-home.php` をロードし、一方で「About」ページには別のファイル (`header-about.php`) をロードし、その他のすべてのページにはデフォルトの `header.php` を適用します。

```php
if ( is_front_page() ) :
	get_header( 'home' );
elseif ( is_page( 'About' ) ) :
	get_header( 'about' );
else:
	get_header();
endif;
```

<!-- 
[You can learn more about Conditional Tags here.](https://developer.wordpress.org/themes/basics/conditional-tags/)
 -->

[「条件付きタグ」の詳細については、こちらをご覧ください](https://developer.wordpress.org/themes/basics/conditional-tags/)。

<!-- 
## Identifying a Page Template
 -->

## ページ・テンプレートの識別

<!-- 
If your template uses the `[body_class()](https://developer.wordpress.org/reference/functions/body_class/)` function, WordPress will print classes in the `body` tag for the post type class name (`page`), the page’s ID (`page-id-{ID}`), and the page template used. For the default `page.php`, the class name generated is `page-template-default`:
 -->

あなたのテンプレートで [`body_class()`](https://developer.wordpress.org/reference/functions/body_class/) 関数を使用している場合、WordPress は、投稿タイプのクラス名 (`page`)、ページの ID (`page-id-{ID}`)、および使用されているページ・テンプレートを示すクラスを、`body` タグ内に出力します。デフォルトの `page.php` の場合、生成されるクラス名は `page-template-default` です:

```markup
<body class="page page-id-6 page-template-default">
```

<!-- 
A specialized template (`page-{slug}.php` or `page-{ID}.php`) also gets the `page-template-default` class rather than its own body class.
 -->

専用テンプレート (`page-{slug}.php` または `page-{ID}.php`) も、独自の body クラスではなく `page-template-default` クラスを取得します。

<!-- 
When using a custom page template, the class `page-template` will print, along with a class naming the specific template. For example, if your custom page template file is named as follows:
 -->

カスタム・ページ・テンプレートを使用する場合、`page-template` クラスと、特定テンプレートを識別するクラス名が、同時に出力されます。たとえば、カスタム・ページ・テンプレート・ファイルが、以下のように命名されている場合:

```php
<?php
/* Template Name: My Custom Page */
?>
```

<!-- 
Then then rendered HTML generated will be as follows:
 -->

その後、生成されるレンダリング済み HTML は、以下のようになります:

```markup
<body class="page page-id-6 page-template page-template-my-custom-page-php">
```

<!-- 
Notice the `page-template-my-custom-page-php` class that is applied to the `body` tag.
 -->

`body` タグに適用されている `page-template-my-custom-page-php` クラスに注意してください。

<!-- 
## Page Template Functions
 -->

## ページ・テンプレート関数

<!-- 
These built-in WordPress functions and methods can help you work with page templates:
 -->

これらのビルトイン WordPress 関数とメソッドは、ページ・テンプレートの操作に役立ちます:

<!-- 
*   `[get_page_template()](https://developer.wordpress.org/reference/functions/get_page_template/)` returns the path of the page template used to render the page.
*   `[wp_get_theme()->get_page_templates()](https://developer.wordpress.org/reference/classes/wp_theme/get_page_templates/)` returns all custom page templates available to the currently active theme (`get_page_templates()` is a method of the `[WP_Theme](https://developer.wordpress.org/reference/classes/wp_theme/)` class).
*   `[is_page_template()](https://developer.wordpress.org/reference/functions/is_page_template/)` returns true or false depending on whether a custom page template was used to render the page.
*   `[get_page_template_slug()](https://developer.wordpress.org/reference/functions/get_page_template_slug/)` returns the value of custom field `_wp_page_template` (`null` when the value is empty or “default”).If a page has been assigned a custom template, the filename of that template is stored as the value of a [custom field](https://codex.wordpress.org/Custom_Fields "Custom Fields") named `'_wp_page_template'` (in the [`wp_postmeta`](https://codex.wordpress.org/Database_Description#Table:_wp_postmeta "Database Description") database table). (Custom fields starting with an underscore do not display in the edit screen’s custom fields module.)
 -->

*   [`get_page_template()`](https://developer.wordpress.org/reference/functions/get_page_template/) は、ページをレンダリングするために使用されたページ・テンプレートのパスを返します。
*   [`wp_get_theme()->get_page_templates()`](https://developer.wordpress.org/reference/classes/wp_theme/get_page_templates/) は、現在有効化されているテーマで使用可能な、すべてのカスタム・ページ・テンプレートを返します (`get_page_templates()` は、[`WP_Theme`](https://developer.wordpress.org/reference/classes/wp_theme/) クラスのメソッド)。
*   [`is_page_template()`](https://developer.wordpress.org/reference/functions/is_page_template/) は、ページをレンダリングするためにカスタム・ページ・テンプレートが使用されたかどうかに応じて、真または偽を返します。
*   [`get_page_template_slug()`](https://developer.wordpress.org/reference/functions/get_page_template_slug/) は、カスタム・フィールド `_wp_page_template` の値を返します (値が空または「default」の場合は、`null` を返す)。ページにカスタム・テンプレートが割り当てられている場合、そのテンプレートのファイル名は、([`wp_postmeta`](https://codex.wordpress.org/Database_Description#Table:_wp_postmeta "Database Description")データベース・テーブル内の)「`_wp_page_template`」という名称の [カスタム・フィールド](https://codex.wordpress.org/Custom_Fields "Custom Fields") の値として保存されます。(アンダースコアで始まるカスタム・フィールドは、編集画面のカスタム・フィールド・モジュールには表示されない)