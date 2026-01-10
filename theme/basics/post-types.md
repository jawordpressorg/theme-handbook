<!--
# Post Types
 -->

# 投稿タイプ

<!--
There are many different types of content in WordPress. These content types are normally described as Post Types, which may be a little confusing since it refers to all different types of content in WordPress. For example, a post is a specific Post Type, and so is a page.
 -->

WordPress には、さまざまな種類のコンテンツが存在します。これらのコンテンツ・タイプは通常「投稿タイプ」と呼ばれますが、これは WordPress 内のあらゆる種類のコンテンツを指すため、少し混乱を招くかもしれません。たとえば、投稿は特定の「投稿タイプ」であり、ページもまた投稿タイプの一つです。

<!--
Internally, all of the Post Types are stored in the same place — in the wp\_posts database table — but are differentiated by a database column called post\_type.
 -->

内部的には、すべての投稿タイプは同じ場所 — `wp_posts` データベース・テーブル — に保存されますが、`post_type` というデータベース列によって区別されます。

<!--
In addition to the default Post Types, you can also create Custom Post Types.
 -->

デフォルトの「投稿タイプ」に加えて、「カスタム投稿タイプ」も作成できます。

<!--
The [Template files](https://developer.wordpress.org/themes/basics/template-files/) page briefly mentioned that different Post Types are displayed by different Template files.  As the whole purpose of a Template file is to display content a certain way, the Post Types purpose is to categorize what type of content you are dealing with. Generally speaking, certain Post Types are tied to certain template files.
 -->

[テンプレート・ファイル](https://developer.wordpress.org/themes/basics/template-files/) ページでは、さまざまな投稿タイプがそれぞれのテンプレート・ファイルによって表示されると、簡単に触れられています。「テンプレート」ファイルの目的は、コンテンツを特定の方法で表示することであるのに対し、「投稿タイプ」の目的は、扱うコンテンツの種類をカテゴライズすることです。一般的に、特定の「投稿タイプ」は、特定のテンプレート・ファイルに関連付けられています。

<!--
## Default Post Types
 -->

## デフォルトの「投稿タイプ」

<!--
There are several default Post Types readily available to users or internally used by the WordPress installation. The most common are:
 -->

WordPress のインストール環境では、ユーザーがすぐに利用できる、あるいは内部で使用されるデフォルトの「投稿タイプ」がいくつか用意されています。最も一般的なものは以下の通りです:

<!--
*   Post (Post Type: ‘post’)
*   Page (Post Type: ‘page’)
*   Attachment (Post Type: ‘attachment’)
*   Revision (Post Type: ‘revision’)
*   Navigation menu (Post Type: ‘nav\_menu\_item’)
*   Block templates (Post Type: ‘wp\_template’)
*   Template parts (Post Type: ‘wp\_template\_part’)
 -->

*   投稿 (投稿タイプ: `post` )
*   固定ページ (投稿タイプ: `page`)
*   添付ファイル (投稿タイプ: `attachment`)
*   リビジョン (投稿タイプ: `revision`)
*   ナビゲーション・メニュー (投稿タイプ: `nav_menu_item`)
*   ブロック・テンプレート (投稿タイプ: `wp_template`)
*   テンプレート・パーツ (投稿タイプ: `wp_template_part`)

<!--
The Post Types above can be modified and removed by a plugin or theme, but it’s not recommended that you remove built-in functionality for a widely-distributed theme or plugin.
 -->

上記の投稿タイプは、プラグインやテーマによって変更や削除ができますが、広く配布されているテーマやプラグインでは、ビルトイン機能を削除することは推奨されません。

<!--
It’s out of the scope of this handbook to explain other post types in detail. However, it is important to note that you will interact with and build the functionality of [navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/) and that will be detailed later in this handbook.
 -->

本ハンドブックの範囲外となるため、その他の投稿タイプについては詳細に説明しません。しかしながら、[ナビゲーション・メニュー](https://developer.wordpress.org/themes/functionality/navigation-menus/) の機能構築や操作する必要がある点に留意してください。これについては、本ハンドブックの後半で詳しく説明します。

<!--
### Post
 -->

### 投稿

<!--
Posts are used in blogs. They are:
 -->

投稿は、ブログで使用されます。それらは:

<!--
*   displayed in reverse sequential order by time, with the newest post first
*   have a date and time stamp
*   may have the default [taxonomies of categories and tags](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) applied
*   are used for creating feeds
 -->

*   時間順に逆順で表示され、最新の投稿が最初に表示されます
*   日付とタイムスタンプが付与されます
*   デフォルトの [カテゴリーとタグのタクソノミー](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) が適用される場合があります
*   フィードの作成に使用されます

<!--
The template files that display the Post post type are:
 -->

投稿タイプ「投稿」を表示するテンプレート・ファイルは、以下の通りです:

<!--
*   `singl`e and `single-post`
*   `category` and all its iterations
*   `tag` and all its iterations
*   `taxonomy` and all its iterations
*   `archive` and all its iterations
*   `author` and all its iterations
*   `date` and all its iterations
*   `search`
*   `home`
*   `index`
 -->

*   `single`、`single-post`
*   `category` と関連するファイル
*   `tag` と関連するファイル
*   `taxonomy` と関連するファイル
*   `archive` と関連するファイル
*   `author` と関連するファイル
*   `date` と関連するファイル
*   `search`
*   `home`
*   `index`

<!--
[Read more about Post Template Files in classic themes](https://developer.wordpress.org/themes/template-files-section/post-template-files/).
 -->

[クラシック・テーマでの、「投稿」テンプレート・ファイルについての詳細は、こちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/post-template-files/)。

<!--
### Page
 -->
### 固定ページ

<!--
Pages are a static Post Type, outside of the normal blog stream/feed. Their features are:
 -->

固定ページは、静的な投稿タイプであり、通常のブログ・ストリーム/フィードとは別物です。その特徴は、以下の通りです:

<!--
*   non-time dependent and without a time stamp
*   are not organized using the categories and/or tags taxonomies
*   can be organized in a hierarchical structure — i.e. pages can be parents/children of other pages
 -->

*   時間依存性がなく、タイムスタンプも付いていません
*   カテゴリーやタグといったタクソノミーを使って編成されていません
*   階層構造で編成できます — たとえば、固定ページは、他の固定ページの親/子にできます

<!--
The template files that display the Page post type are:
 -->

投稿タイプ「ページ」を表示するテンプレート・ファイルは、以下の通りです:

<!--
*   `page` and all its iterations
*   `front-page`
*   `search`
*   `index`
 -->

*   `page` と関連するファイル
*   `front-page`
*   `search`
*   `index`

<!--
[Read more about Page Template Files in classic themes](https://developer.wordpress.org/themes/template-files-section/page-template-files/).
 -->

[クラシック・テーマでの、「固定ページ」テンプレート・ファイルについての詳細は、こちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/page-template-files/)。

<!--
### Attachment
 -->

### 添付ファイル

<!--
Attachments are commonly used to display images or media in content, and may also be used to link to relevant files. Their features are:
 -->

添付ファイルは、コンテンツ内で画像やメディアを表示するために一般的に使用され、関連ファイルへのリンクとしても使用される場合があります。その特徴は、以下の通りです:

<!--
*   contain information (such as name or description) about files uploaded through the media upload system
*   for images, this includes metadata information stored in the wp\_postmeta table (including size, thumbnails, location, etc)
 -->

*   メディア・アップロード・システムを通じてアップロードされた、ファイルに関する情報 (名称や説明など) を含む
*   画像の場合、これには `wp_postmeta` テーブルに保存される、メタデータ情報 (サイズ、サムネイル、保存場所など) が該当する

<!--
The template files that display the Attachment post type are:
 -->

投稿タイプ「添付ファイル」を表示するテンプレート・ファイルは、以下の通りです:

*   `MIME_type`
*   `attachment`
*   `single-attachment`
*   `single`
*   `index`

<!--
[Read more about Attachment Template Files in classic themes](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/).
 -->

[クラシック・テーマでの、「添付ファイル」テンプレート・ファイルについての詳細は、こちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/)。

<!--
## Custom Post Types
 -->
## カスタム投稿タイプ

<!--
Using Custom Post Types, you can **create your own post type**. It is not recommend that you place this functionality in your theme. This type of functionality should be placed/created in a plugin. This ensures the portability of your user’s content, and that if the theme is changed the content stored in the Custom Post Types won’t disappear.
 -->

「カスタム投稿タイプ」を使用すると、**独自の投稿タイプを作成** できます。この機能をあなたのテーマ内に組み込むことは、推奨されません。この種の機能は、プラグイン内で実装/作成すべきです。これによりあなたのユーザーのコンテンツの移植性が確保され、テーマを変更しても、「カスタム投稿タイプ」に保存されたコンテンツが消失することは、ありません。

<!--
You can learn more about [creating custom post types in the WordPress Plugin Developer Handbook](https://developer.wordpress.org/plugins/post-types/registering-custom-post-types/).
 -->

[WordPress プラグイン開発者ハンドブックで、カスタム投稿タイプの作成](https://developer.wordpress.org/plugins/post-types/registering-custom-post-types/) についての詳細を学ぶことができます。

<!--
While you generally won’t develop Custom Post Types in your theme, you may want to code ways to display Custom Post Types that were created by a plugin.  The following templates can display Custom post types:
 -->

通常、あなたのテーマ内で「カスタム投稿タイプ」を開発することはありませんが、プラグインによって作成された「カスタム投稿タイプ」を表示する方法をコーディングしたい場合があるかもしれません。以下のテンプレートは、「カスタム」投稿タイプを表示できます:

*   `single-{post-type}`
*   `archive-{post-type}`
*   `search`
*   `index`

<!--
[Read more about Custom Post Type Templates in classic themes](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/).
 -->

[クラシック・テーマでの、「カスタム投稿タイプ」テンプレート・ファイルについての詳細は、こちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/)。