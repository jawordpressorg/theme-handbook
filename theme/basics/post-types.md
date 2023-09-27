<!--
# Post Types
-->
# 投稿タイプ

<!--
There are many different types of content in WordPress. These content types are normally described as Post Types, which may be a little confusing since it refers to all different types of content in WordPress. For example, a post is a specific Post Type, and so is a page.
-->
WordPress にはさまざまな種類のコンテンツがあり、これらのコンテンツのことを「投稿タイプ」と呼びます。ただし、WordPress にあるさまざまな種類のコンテンツをのことも投稿タイプと呼ぶため、少し混乱するかもしれません。たとえば、投稿は投稿タイプのひとつですが、固定ページも同様に投稿タイプと呼びます。

<!--
Internally, all of the Post Types are stored in the same place — in the wp\_posts database table — but are differentiated by a database column called post\_type.
-->
内部的にはどのような投稿タイプでもすべて同じ場所 (データベースの `wp_posts` テーブル) に保存されていて、 `post_type` カラムによって区別されます。

<!--
In addition to the default Post Types, you can also create Custom Post Types.
-->
デフォルトの投稿タイプに加えて、カスタム投稿タイプも作成できます。

<!--
The [Template files](https://developer.wordpress.org/themes/basics/template-files/) page briefly mentioned that different Post Types are displayed by different Template files.  As the whole purpose of a Template file is to display content a certain way, the Post Types purpose is to categorize what type of content you are dealing with. Generally speaking, certain Post Types are tied to certain template files.
-->
[テンプレートファイル](https://developer.wordpress.org/themes/basics/template-files/)のページでは、投稿タイプはそれぞれ対応するテンプレートファイルで表示されると説明しました。投稿タイプは扱っているコンテンツの種類を分類するためのものであり、テンプレートファイルはそれにもとづいてコンテンツを表示するものです。一般的には、特定の投稿タイプと特定のテンプレートファイルは紐づいています。

<!--
## Default Post Types
-->
## デフォルトの投稿タイプ

<!--
There are several default Post Types readily available to users or internally used by the WordPress installation. The most common are:
-->
WordPress をインストールした際に利用可能な標準の投稿タイプがいくつかあります。主要なものは次のとおりです:

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
*   ナビゲーションメニュー (投稿タイプ: `nav_menu_item`)
*   ブロックテンプレート (投稿タイプ: `wp_template`)
*   テンプレートパーツ (投稿タイプ: `wp_template_part`)

<!--
The Post Types above can be modified and removed by a plugin or theme, but it’s not recommended that you remove built-in functionality for a widely-distributed theme or plugin.
-->
上記の投稿タイプはテーマやプラグインで変更したり削除できますが、広く配布する予定のテーマやプラグインにおいて WordPress に組み込まれた機能を削除することは推奨されません。

<!--
It’s out of the scope of this handbook to explain other post types in detail. However, it is important to note that you will interact with and build the functionality of [navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/) and that will be detailed later in this handbook.
-->
このハンドブックではその他の投稿タイプについて詳しく説明しませんが、[ナビゲーションメニュー](https://developer.wordpress.org/themes/functionality/navigation-menus/)の機能を操作して構築する事は重要であり、これについてはこのハンドブックでのちほど詳しく説明します。

<!--
### Post
-->
### 投稿 (post)

<!--
Posts are used in blogs. They are:
-->
投稿はブログでよく使われます。

<!--
*   displayed in reverse sequential order by time, with the newest post first
*   have a date and time stamp
*   may have the default [taxonomies of categories and tags](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) applied
*   are used for creating feeds
-->
*   最も新しい投稿が最初となるように、逆時系列順に表示されます
*   日付と時間が設定されています
*   デフォルトの[タクソノミーであるカテゴリとタグ](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/)が適用できます
*   フィードの作成に使われます

<!--
The template files that display the Post post type are:
-->
投稿を表示するテンプレートファイルは次のとおりです:

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
[クラシックテーマでの投稿テンプレートファイルについてはこちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/post-template-files/)。

<!--
### Page
-->
### 固定ページ (page)

<!--
Pages are a static Post Type, outside of the normal blog stream/feed. Their features are:
-->
固定ページは通常のブログフィードとは違って、静的な投稿タイプです。その特徴は以下の通りです:

<!--
*   non-time dependent and without a time stamp
*   are not organized using the categories and/or tags taxonomies
*   can be organized in a hierarchical structure — i.e. pages can be parents/children of other pages
-->
*   時系列に表示されません
*   カテゴリーやタグといったタクソノミーで分類されません
*   ある固定ページが他の固定ページを親に持つ階層化した構造にできます

<!--
The template files that display the Page post type are:
-->
固定ページを表示するテンプレートファイルは次のとおりです:

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
[クラシックテーマでの固定ページテンプレートファイルについてはこちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/page-template-files/)。

<!--
### Attachment
-->
### 添付ファイル (attachment)

<!--
Attachments are commonly used to display images or media in content, and may also be used to link to relevant files. Their features are:
-->
添付ファイルはコンテンツの中で画像やメディアを表示する際に使用し、関連するファイルへのリンクとしても使用されます。

<!--
*   contain information (such as name or description) about files uploaded through the media upload system
*   for images, this includes metadata information stored in the wp\_postmeta table (including size, thumbnails, location, etc)
-->
*   WordPress のメディアアップロードシステムを使ってアップロードされたファイルについて、ファイル名や説明などの情報を保持します
*   画像ファイルの場合、 `wp_postmeta` テーブルで保持されるファイルの情報も含みます (画像サイズ・サムネイル・ファイルの保存場所など)

<!--
The template files that display the Attachment post type are:
-->
添付ファイルを表示するテンプレートファイルは次のとおりです:

*   `MIME_type`
*   `attachment`
*   `single-attachment`
*   `single`
*   `index`

<!--
[Read more about Attachment Template Files in classic themes](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/).
-->
[クラシックテーマでの添付ファイルテンプレートファイルについてはこちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/attachment-template-files/)。

<!--
## Custom Post Types
-->
## カスタム投稿タイプ

<!--
Using Custom Post Types, you can **create your own post type**. It is not recommend that you place this functionality in your theme. This type of functionality should be placed/created in a plugin. This ensures the portability of your user’s content, and that if the theme is changed the content stored in the Custom Post Types won’t disappear.
-->
カスタム投稿タイプを使うと**独自の「投稿タイプ」を作成**できます。カスタム投稿タイプはテーマ内ではなく、プラグイン内で定義することを強くおすすめします。そうすればテーマを切り替えてもカスタム投稿タイプのコンテンツが消えることなく他のテーマでも使い続けることができます。

<!--
You can learn more about [creating custom post types in the WordPress Plugin Developer Handbook](https://developer.wordpress.org/plugins/post-types/registering-custom-post-types/).
-->
カスタム投稿タイプの作成については、[プラグイン開発ハンドブック](https://developer.wordpress.org/plugins/post-types/registering-custom-post-types/)をご覧ください。

<!--
While you generally won’t develop Custom Post Types in your theme, you may want to code ways to display Custom Post Types that were created by a plugin.  The following templates can display Custom post types:
-->
一般的にテーマ内でカスタム投稿タイプを新たに作ることはないものの、プラグインによって作られたカスタム投稿タイプを表示するために、カスタム投稿タイプを扱えるようにしておくことをおすすめします。次のテンプレートファイルでカスタム投稿タイプを表示できます:

*   `single-{post-type}`
*   `archive-{post-type}`
*   `search`
*   `index`

<!--
[Read more about Custom Post Type Templates in classic themes](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/).
-->
[クラシックテーマでのカスタム投稿タイプのテンプレートファイルについてはこちらをご覧ください](https://developer.wordpress.org/themes/template-files-section/custom-post-type-template-files/)。
