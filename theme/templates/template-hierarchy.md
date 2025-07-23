<!-- 
# Template Hierarchy
 -->

# テンプレート階層

<!-- 
As covered in the [Templates](https://developer.wordpress.org/themes/templates/templates/) documentation, templates are reusable files that are used to generate the document structure of pages on your WordPress site. WordPress’ template loader determines which template file should be loaded on any given URL.
 -->

[テンプレート](https://developer.wordpress.org/themes/templates/templates/) ドキュメントで説明したように、テンプレートは、あなたの WordPress サイトのページのドキュメント構造を生成するために使用される、再利用可能なファイルです。WordPress のテンプレート・ローダは、どんな URL でも、どのテンプレート・ファイルを読み込むべきかを決定します。

<!-- 
This document explains how WordPress’ template loader uses the queried information for a page to build a template hierarchy. Then it covers what the valid templates are for the hierarchy.
 -->

このドキュメントでは、WordPress のテンプレート・ローダが、クエリーされたページの情報を使ってテンプレート階層を構築する方法を説明します。その後、その階層に対して適切なテンプレートについて説明します。

<!-- 
## Overview
 -->

## 概要

<!-- 
When a visitor lands on any page on a WordPress site, WordPress uses the [query string](https://wordpress.org/documentation/article/wordpress-glossary/#query-string) to decide which template should be used to display the page. The query string contains data from the URL that helps make this determination.
 -->

訪問者が WordPress サイトのページにアクセスすると、WordPress は [クエリー文字列](https://wordpress.org/documentation/article/wordpress-glossary/#query-string) を使って、ページを表示すべきテンプレートを決定します。クエリー文字列には、この決定に役立つ URL に由来するデータが含まれています。

<!-- 
With this data available, WordPress searches through the template hierarchy until it finds a matching template file. There are generally three potential areas that WordPress might look for a block template within the hierarchy (in order of priority):
 -->

このデータをもとに、WordPress はテンプレート階層を検索し、合致するテンプレート・ファイルを見つけます。WordPress が階層内でブロック・テンプレートを探す可能性のある領域は、一般的に3つあります (リストは優先度順):

<!-- 
*   User-created templates stored under the `wp_template` post type in the database.
*   Templates located in a child theme’s `/templates` folder (if child theme is active).
*   Templates in the theme’s `/templates` folder.
 -->

*   データベースの `wp_template` 投稿タイプ下に保存された、ユーザー制作テンプレート。
*   (子テーマが有効化されている場合) 子テーマの `/templates` フォルダーにあるテンプレート。
*   テーマの `/templates` フォルダーにあるテンプレート。

<!-- 
Your theme can package as many or as few templates as needed to achieve your theme design. The `index.html` template is the only required template file for a block theme.
 -->

あなたのテーマは、あなたのテーマ設計を実現するために必要な数のテンプレートを、パッケージ化できます。`index.html` テンプレートはブロック・テーマに必要な唯一のテンプレート・ファイルです。

<!-- 
## Visual overview
 -->

## ビジュアルな概要

<!-- 
This diagram shows which template files are called to generate a WordPress page based on the template hierarchy:
 -->

この図は、テンプレート階層にもとづいて WordPress ページを生成するために、どのテンプレート・ファイルが呼び出されるかを示しています:

<!-- 
[![Visual diagram of the WordPress template hierarchy.](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-hierarchy-scaled.jpeg?resize=2560%2C1404&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-hierarchy-scaled.jpeg?ssl=1)
 -->

[![WordPress テンプレート階層の視覚的な図。](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-hierarchy-scaled.jpeg?resize=2560%2C1404&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/template-hierarchy-scaled.jpeg?ssl=1)

<!-- 
## The template hierarchy by query type
 -->

## クエリータイプによるテンプレート階層

<!-- 
In WordPress, there is not technically a single template hierarchy. It’s best to think of the hierarchy by the type of page being queried. For example, if the front page is being queried, then it will use the front page template hierarchy.
 -->

WordPress では、技術的にはテンプレートの階層は単一ではありません。クエリーされるページのタイプによって階層を考えるのがベストです。たとえば、フロントページがクエリーされる場合、フロントページのテンプレート階層を使用します。

<!-- 
Below, you will find each template hierarchy broken down by its query type (and some subtypes). This will help you determine which template files to include in your theme.
 -->

以下に、各テンプレートの階層をクエリータイプ (およびいくつかのサブタイプ) 別に分類しています。これは、どのテンプレート・ファイルをあなたのテーマに含めるかを決めるのに役立ちます。

<!-- 
### Front page hierarchy
 -->

### 「フロントページ」階層

<!-- 
The Front Page template hierarchy is unique among templates and can change drastically based on what the user has chosen for their **Front page displays** setting under **Settings > Reading** in the admin.
 -->

「フロントページ」のテンプレート階層はテンプレートの中でも独特で、ユーザーが管理画面の **設定 > 表示設定** で **ホームページの表示** 設定に何を選んだかによって大きく変わります。

<!-- 
If **Your latest posts** is chosen for the **Front page displays** setting, the hierarchy is:
 -->

**ホームページの表示** 設定で、**最新の投稿** を選択した場合、階層は次のようになります:

<!-- 
*   `front-page.html`
*   Falls back to the [Home template hierarchy](#home-hierarchy)
 -->

*   `front-page.html`
*   [「ホーム」テンプレート階層](#home-hierarchy) にフォールバック

<!-- 
If **A static page** is chosen for the **Front page displays** setting, the hierarchy is:
 -->

**ホームページの表示** 設定で、**固定ページ** を選択した場合、階層は次のようになります:

<!-- 
*   `front-page.html`
*   Falls back to the [Page template hierarchy](#page-hierarchy)
 -->

*   `front-page.html`
*   [「ページ」テンプレート階層](#page-hierarchy) にフォールバック

<!-- 
Keep in mind that the `front-page.html` template always takes precedence, regardless of the **Front page displays** setting. It is only the templates lower in the hierarchy that are affected by it.
 -->

**ホームページの表示** 設定に関係なく、`front-page.html` テンプレートが常に優先されることに留意してください。その影響を受けるのは、階層の低いテンプレートだけなのです。

<!-- 
### Home hierarchy
 -->

### 「ホーム」階層

<!-- 
Despite its name, the Home template is not always used for the homepage of a site. Technically, it refers to the page where your latest blog posts are shown (i.e., the blog posts index). 
 -->

その名前とは裏腹に、「ホーム」テンプレートは必ずしもサイトのトップページに使われるとは限りません。技術的には、あなたの最新のブログ記事が表示されるページ (例: ブログ投稿のインデックス) を指します。

<!-- 
Like the Front Page template hierarchy, the Home template also depends on the **Front page displays** setting under **Settings > Reading** in the admin. 
 -->

「フロントページ」テンプレート階層と同様に、「ホーム」テンプレートも管理画面の **設定 > 表示設定** 下の **ホームページの表示** 設定に依存します。

<!-- 
If **Your latest posts** is chosen for the **Front page displays** setting, this hierarchy will be applied to the front page of the site:
 -->

**ホームページの表示** 設定で **最新の投稿** を選択した場合、この階層は、サイトのフロントページに適用されます:

*   `front-page.html`
*   `home.html`
*   `index.html`

<!-- 
If **A static page** is chosen for the **Front page displays** setting and a page is selected for **Posts page** setting, the Home template hierarchy applies to the selected posts page (it does not apply to the front page in this case). The hierarchy in this scenario is:
 -->

**ホームページの表示** 設定で **固定ページ** を選択し、**投稿ページ** 設定でページを選択した場合、「ホーム」テンプレート階層は、選択された投稿ページに適用されます (この場合、フロントページには適用されない)。このシナリオでの階層は:

*   `home.html`
*   `index.html`

<!-- 
**Some history:** The term “home” goes back to WordPress’ earliest days when it was only a blogging system and the only thing that appeared on the site’s front page was blog posts. While WordPress has evolved to allow anything on the front page, the “home” terminology was retained to refer to the blog posts index. And the “front page” terminology was used to refer to the site’s front page.
 -->

**歴史:**「ホーム」という用語は、WordPress がまだブログ・システムであり、サイトのフロントページに表示されるのはブログ投稿だけだった初期のころにまでさかのぼります。WordPress が進化してフロントページに何でも表示できるようになった一方で、「ホーム」という用語は、ブログ投稿のインデックスを指すために、そのまま引き継がれることになりました。そして、「フロントページ」という用語は、サイトのフロントページを指すために用いられます。

<!-- 
### Singular hierarchy
 -->

### 「単一ページ」階層

<!-- 
When a visitor lands on a single post, page, attachment page, or entry from a custom post type, WordPress attempts to locate a template based on the queried post for that view.
 -->

訪問者が個別投稿、ページ、添付ページ、またはカスタム投稿タイプからのエントリーにアクセスすると、WordPress はその表示用にクエリーされた投稿にもとづいてテンプレートを見つけようとします。

<!-- 
All singular templates can utilize a custom template, which you’ll see listed as `{custom_template}.html` in the sub-sections below. These almost always sit at the top of the hierarchy. For more information on creating custom templates, check out the “Custom Templates” section of the main [Templates](https://developer.wordpress.org/themes/templates/templates/) documentation.
 -->

すべての単一ページテンプレートは、以下のサブセクションで `{custom_template}.html` とリストされているカスタム・テンプレートを利用できます。これらはほとんどの場合、階層の最上位に位置します。カスタム・テンプレート制作に関する詳細情報は、メインの [テンプレート](https://developer.wordpress.org/themes/templates/templates/) ドキュメントの、「カスタム・テンプレート」セクションをご覧ください。

<!-- 
#### Single hierarchy
 -->

#### 「個別投稿」階層

<!-- 
The Single template hierarchy is fired when a visitor lands upon a single post or a single entry from a custom post type. The following hierarchy is used to determine the template:
 -->

「個別投稿」テンプレート階層は、訪問者が個別投稿、もしくはカスタム投稿タイプからの個別エントリーにアクセスした際に発生します。テンプレートを決定するために、次の階層が使われます:

*   `{custom-template}.html`
*   `single-{post_type}-{post_name}.html`
*   `single-{post_type}.html`
*   `single.html`
*   `singular.html`
*   `index.html`

<!-- 
A custom post type of `product` with a post name (i.e., slug) of `blue-shirt` would use this hierarchy:
 -->

カスタム投稿タイプが `product` で、投稿名 (例: スラッグ) が `blue-shirt` の場合、この階層を使うことになります:

*   `{custom-template}.html`
*   `single-product-blue-shirt.html`
*   `single-product.html`
*   `single.html`
*   `singular.html`
*   `index.html`

<!-- 
The core WordPress `page` and `attachment` post types are special cases and are handled differently from the default Single template hierarchy. See the below Page and Attachment sections for more details.
 -->

コア WordPress `page` と `attachment` 投稿タイプは特殊ケースであり、デフォルト「個別投稿」テンプレート階層とは異なる扱いになります。詳細については、「ページ」セクションと「添付ファイル」セクションをご覧ください。

<!-- 
#### Page hierarchy
 -->

#### 「ページ」階層

<!-- 
The Page template hierarchy fires when someone visits a single page on your website. This hierarchy is used to determine the template:
 -->

「ページ」テンプレート階層は、誰かがあなたの Web サイトの個別投稿ページを訪問した際に発生します。この階層は、テンプレートを決定するために使用されます:

*   `{custom-template}.html`
*   `page-{post_name}.html`
*   `page-{post_id}.html`
*   `page.html`
*   `index.html`

<!-- 
A page with a post name (i.e., slug) of `about-me` and an ID of `200` would use this hierarchy:
 -->

投稿名 (例: スラッグ) が `about-me` で、ID が `200` のページは、この階層を使うことになります:

*   `{custom-template}.html`
*   `page-about-me.html`
*   `page-200.html`
*   `page.html`
*   `index.html`

<!-- 
#### Attachment (media) hierarchy
 -->

#### 「添付ファイル (メディア)」階層

<!-- 
When visiting the singular views for attachments (media file pages), WordPress prepends the default Single template hierarchy with some additional templates. This is the Attachment template hierarchy:
 -->

添付ファイル (メディアファイル・ページ) 用の個別ページ表示を訪問する際、WordPress はデフォルト「個別投稿」テンプレート階層の前に、いくつかの追加テンプレートを追加します。これが「添付ファイル」テンプレート階層です:

<!-- 
*   `{mime_type}-{sub_type}.html`
*   `{sub_type}.html`
*   `{mime_type}.html`
*   `attachment.html`
*   Falls back to the default [Single template hierarchy](#single-hierarchy)
 -->

*   `{mime_type}-{sub_type}.html`
*   `{sub_type}.html`
*   `{mime_type}.html`
*   `attachment.html`
*   デフォルト[「個別投稿」テンプレート階層](#single-hierarchy) にフォールバック

<!-- 
If you had an attachment with the `image/jpeg` mime type, the `image` piece of that would be considered the `mime_type`, and the `jpeg` part would be the `sub_type`.
 -->

mime タイプ `image/jpeg` の添付ファイルがあった場合、`image` の部分は `mime_type`、`jpeg` の部分は `sub_type` と見なされるでしょう。

<!-- 
Suppose you had an attachment with the `image/jpeg` type and the post name (i.e., slug) of `red-bird`. The full attachment template hierarchy would be:
 -->

`image/jpeg` タイプで投稿名 (例: スラッグ) が `red-bird` の添付ファイルがあったとします。添付ファイルのテンプレート階層は次のようになります:

*   `image-jpeg.html`
*   `jpeg.html`
*   `image.html`
*   `attachment.html`
*   `{custom-template}.html`
*   `single-attachment-red-bird.html`
*   `single-attachment.html`
*   `single.html`
*   `singular.html`
*   `index.html`

<!-- 
As of WordPress 6.4, attachment pages are [no longer enabled by default](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/) on new installations. Users can enable them with a plugin, so it is still good practice to test your theme and ensure it properly displays content when viewing an attachment page.
 -->

WordPress 6.4以降、添付ページは新規インストール時には [もはや、デフォルトでは有効ではない](https://make.wordpress.org/core/2023/10/16/changes-to-attachment-pages/) です。ユーザーはプラグインを使用してこれらを有効化できるので、添付ファイルページを表示する際には、テーマをテストし、コンテンツが適切に表示されることを確認するのが良い慣習です。

<!-- 
#### Privacy Policy page hierarchy
 -->

#### 「個人情報保護方針」ページ階層

<!-- 
The Privacy Policy page in WordPress is a special case in comparison to other pages. WordPress will look for a `privacy-policy.html` template before looking at the normal page template hierarchy. For the Privacy Policy page, the following is the template hierarchy:
 -->

WordPress の「個人情報保護方針」ページは、他のページと比べて特殊なケースです。WordPress は、通常の「ページ」テンプレート階層を見る前に、`privacy-policy.html` テンプレートを探します。「個人情報保護方針」ページの場合、テンプレート階層は以下のようになります:

<!-- 
*   `privacy-policy.html`
*   Falls back to the [Page template hierarchy](#page-hierarchy)
 -->

*   `privacy-policy.html`
*   [「ページ」テンプレート階層](#page-hierarchy) にフォールバック

<!-- 
### Archive hierarchy
 -->

### 「アーカイブ」階層

<!-- 
Archives in WordPress display posts that are grouped by either some type of metadata (e.g., date, author, post type) or by a taxonomy term (category, tag).
 -->

WordPress のアーカイブは、何らかのメタデータ (例: 日時、作者、投稿タイプ) またはタクソノミー・ターム (カテゴリー、タグ) によってグループ化された投稿を表示します。

<!-- 
#### Taxonomy term hierarchy
 -->

#### 「タクソノミー・ターム」階層

<!-- 
When working with publicly-rendered taxonomies, each term within the taxonomy will have its own archive page. The taxonomy term template hierarchy is:
 -->

公開されているタクソノミーを使用する場合、タクソノミーの各タームは独自のアーカイブ・ページを持ちます。「タクソノミー・ターム」テンプレート階層は以下の通りです:

*   `taxonomy-{taxonomy_slug}-{term_slug}.html`
*   `taxonomy-{taxonomy_slug}.html`
*   `taxonomy.html`
*   `archive.html`
*   `index.html`

<!-- 
If you had a taxonomy with the slug of `location` and a term within that taxonomy with the slug of `alabama`, the template hierarchy would become:
 -->

`location` というスラッグのタクソノミーと、そのタクソノミー内の `alabama` というスラッグのタームがあった場合、テンプレート階層は次のようになります:

*   `taxonomy-location-alabama.html`
*   `taxonomy-location.html`
*   `taxonomy.html`
*   `archive.html`
*   `index.html`

<!-- 
The core WordPress `category` and `post_tag` taxonomies do not use the taxonomy term template. See the Category and Tag sections below for more details.
 -->

コア WordPress `category` と `post_tag` タクソノミーは、「タクソノミー・ターム」テンプレートを使用しません。詳細については、以下の「カテゴリー」セクションと「タグ」セクションを参照してください。

<!-- 
#### Category hierarchy
 -->

#### 「カテゴリー」階層

<!-- 
When a visitor clicks on a category link and views the category archive page, the following template hierarchy is used:
 -->

訪問者がカテゴリー・リンクをクリックし、カテゴリー・アーカイブ・ページを表示すると、以下のテンプレート階層が使用されます:

*   `category-{slug}.html`
*   `category-{id}.html`
*   `category.html`
*   `archive.html`
*   `index.html`

<!-- 
When viewing a category archive where the category slug is `news` and the category ID is `123`, the template hierarchy becomes:
 -->

カテゴリーのスラッグが `news` で、カテゴリー ID が `123` であるカテゴリー・アーカイブを表示する際、テンプレート階層は次のようになります:

*   `category-news.html`
*   `category-123.html`
*   `category.html`
*   `archive.html`
*   `index.html`

<!-- 
#### Tag hierarchy
 -->

#### 「タグ」階層

<!-- 
When a visitor clicks on a tag link and views a tag archive page, the following template hierarchy is used:
 -->

訪問者がタグ・リンクをクリックし、タグ・アーカイブ・ページを表示すると、以下のテンプレート階層が使用されます:

*   `tag-{slug}.html`
*   `tag-{id}.html`
*   `tag.html`
*   `archive.html`
*   `index.html`

<!-- 
When viewing a tag archive where the tag slug is `flowers` and the tag ID is `456`, the template hierarchy becomes:
 -->

タグのスラッグが `flowers` で、タグ ID が `456` であるタグ・アーカイブを表示する際、テンプレート階層は次のようになります:

*   `tag-flowers.html`
*   `tag-456.html`
*   `tag.html`
*   `archive.html`
*   `index.html`

<!-- 
#### Post type archive hierarchy
 -->

#### 「投稿タイプ・アーカイブ」階層

<!-- 
A custom post type can have a publicly-facing archive page, which essentially serves as an index page for that post type, listing its latest posts by default (though, this can be filtered and changed). When a visitor views a post type archive, the template hierarchy is:
 -->

カスタム投稿タイプは、公開用のアーカイブページを持つことができ、このページは、基本的にその投稿タイプのインデックスページとして機能し、デフォルトでは最新の投稿を一覧表示します (ただし、これはフィルタリングして変更できる)。訪問者が投稿タイプ・アーカイブを表示する際、テンプレート階層は次のようになります:

*   `archive-{post_type}.html`
*   `archive.html`
*   `index.html`

<!-- 
If you had a post type with the slug of `portfolio_project`, its hierarchy would be:
 -->

`portfolio_project` というスラッグを持つ投稿タイプがあった場合、その階層は次のようになります:

*   `archive-portfolio_project.html`
*   `archive.html`
*   `index.html`

<!-- 
The core WordPress `post` post type uses the [Home template hierarchy](#home-hierarchy), and the default `page` and `attachment` post types do not have archive views.
 -->

コア WordPress `post` 投稿タイプは [「ホーム」テンプレート階層](#home-hierarchy) を使用し、デフォルト `page` と `attachment` 投稿タイプにはアーカイブ表示がありません。

<!-- 
#### Author hierarchy
 -->

#### 「作者」階層

<!-- 
Despite its use of the term “author,” an author archive is one part user profile and one part post author archives. An archive URL is generated for all users on a WordPress site, regardless of whether they have published posts. But the intent of the author template is generally to display some metadata about the user and list their posts.
 -->

「作者」という用語を使用していますが、作者アーカイブはユーザープロフィールと投稿の作者アーカイブの一部です。アーカイブ URL は、WordPress サイト上のすべてのユーザーに対して、公開した投稿の有無にかかわらず生成されます。しかし、「作者」テンプレートの意図は一般的に、ユーザーに関するいくつかのメタデータを表示し、その投稿を一覧表示することです。

<!-- 
When visiting an author archive page on the front end of a site, this is the template hierarchy:
 -->

サイトのフロントエンドで作者アーカイブページにアクセスする際、これがテンプレート階層となります:

*   `author-{user_nicename}.html`
*   `author-{user_id}.html`
*   `author.html`
*   `archive.html`
*   `index.html`

<!-- 
When visiting an author archive page for a user with a nicename of `matt` and an ID of `333`, the author archive template hierarchy becomes:
 -->

`matt` というニックネームと `333` という ID を持つユーザーの「作者」アーカイブ・ページにアクセスした際、「作者アーカイブ」テンプレート階層は次のようになります:

*   `author-matt.html`
*   `author-333.html`
*   `author.html`
*   `archive.html`
*   `index.html`

<!-- 
#### Date hierarchy
 -->

#### 「日時」階層

<!-- 
When viewing a date or datetime-based archive page (e.g., yearly, monthly, weekly archives), The template hierarchy is:
 -->

日付または日時ベースのアーカイブページ (例: 年間アーカイブ、月間アーカイブ、週間アーカイブ) を表示する際、テンプレート階層は次のようになります:

*   `date.html`
*   `archive.html`
*   `index.html`

<!-- 
### Search hierarchy
 -->

### 「検索結果」階層

<!-- 
The search template hierarchy is used when viewing the search results on your website. It is similar to archives in that it lists multiple posts, but it is not technically an archive page. The template hierarchy for search results is:
 -->

「検索」テンプレート階層は、あなたの Web サイトで検索結果を表示する際に使用されます。複数の投稿を一覧表示するという点ではアーカイブに似ていますが、技術的にはアーカイブページではありません。検索結果のテンプレート階層は:

*   `search.html`
*   `index.html`

<!-- 
### 404 (not found) hierarchy
 -->

### 「404 (見つかりません)」階層

<!-- 
When a URL is visited on the website that doesn’t exist, WordPress looks for a 404 template, which is intended to provide some helpful information about the page not existing. The template hierarchy for 404 pages is:
 -->

存在しない URL にアクセスした際、WordPress は「404」テンプレートを探しますが、存在しないページに関する有益な情報を提供するためのものです。「404」ページのテンプレート階層は以下の通りです:

*   `404.html`
*   `index.html`

<!-- 
### Embed hierarchy
 -->

### 「埋め込み」階層

<!-- 
The embed template is used when one site embeds a post from your WordPress site. WordPress wraps the output in an `<iframe>` and displays the embedded content according to the template.
 -->

「埋め込み」テンプレートは、あるサイトがあなたの WordPress サイトから投稿を埋め込む際に使用されます。WordPress は出力を `<iframe>` で囲み、テンプレートに従って埋め込みコンテンツを表示します。

<!-- 
[Embed templates are not supported](https://github.com/WordPress/gutenberg/issues/47717) by the block templates system. To build and use custom embed templates, they must be located in your theme’s root folder and use the PHP file extension.
 -->

ブロック・テンプレート・システムでは、[「埋め込み」テンプレートは未対応](https://github.com/WordPress/gutenberg/issues/47717) です。カスタム埋め込みテンプレートを作成して使用するには、テーマのルートフォルダーに配置し、PHP 拡張子を使用する必要があります。

<!-- 
The template hierarchy for embedded content is:
 -->

埋め込みコンテンツのテンプレート階層は、以下の通りです:

*   `embed-{post_type}-{post_format}.php`
*   `embed-{post_type}.php`
*   `embed.php`

<!-- 
If a custom embed template is not included in the theme, WordPress will use the `/wp-includes/theme-compat/embed.php` template bundled with core. It does not fall back to the index template like other template types.
 -->

カスタム埋め込みテンプレートがテーマに含まれていない場合、WordPress はコアにバンドルされている `/wp-includes/theme-compat/embed.php` テンプレートを使用します。他のテンプレートタイプのように「インデックス」テンプレートにフォールバックすることはありません。

<!-- 
If you were embedding a post with a post type of `post` and the post format of `image`, the hierarchy becomes:
 -->

投稿タイプが `post` で、投稿フォーマットが `image` の投稿を埋め込む際、階層は次のようになります:

*   `embed-post-image.php`
*   `embed-post.php`
*   `embed.php`