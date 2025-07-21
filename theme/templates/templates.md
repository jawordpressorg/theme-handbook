<!-- 
# Templates
 -->

# テンプレート

<!-- 
Templates are one of the most important aspects of theme development. They are files that you put together to represent the document structure that appears on the front end of a website. When combined with [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) (`theme.json`), you can ultimately create a unique design to use for yourself, clients, or just share with the world.
 -->

テンプレートは、テーマ開発において最も重要な要素のひとつです。これは、Web サイトのフロントエンドに表示される文書構造を表現するためにまとめるファイルです。[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) (`theme.json`) と組み合わせることで、最終的に独自のデザインを制作し、自分自身やクライアントのために使用したり、世界と共有したりできます。

<!-- 
Templates are how you decide where things are placed within your theme. 
 -->

テンプレートは、あなたのテーマ内のどこに何を配置するかを決める手段です。

<!-- 
*Want a giant footer at the bottom of the site?* You can do that by adding specific blocks inside a Group block at the bottom of a template.
 -->

*サイトの最下部に巨大なフッターが欲しいですか ?* テンプレートの最下部にあるグループブロックの中に特定のブロックを追加することで実現できます。

<!-- 
*Want a sidebar next to the content area?* No problem. You can put a Columns block in one or more of your templates to create that layout.
 -->

*コンテンツ・エリアの隣にサイドバーが欲しいですか ?* 問題ありません。1つまたは複数のあなたのテンプレートに「カラム」ブロックを設置して、そのレイアウトを制作できます。

<!-- 
In [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/), you gained a broad overview of how the WordPress templating system works. In this document, we’ll dive more deeply into the templates themselves.
 -->

[テンプレート入門](https://developer.wordpress.org/themes/templates/introduction-to-templates/) では、WordPress のテンプレート・システムのしくみについて、大まかな概要を説明しました。このドキュメントでは、テンプレートそのものについてより深く掘り下げていきます。

<!-- 
## How do templates work?
 -->

## テンプレートのしくみって ?

<!-- 
Whenever someone visits any page on your site, WordPress takes a look at the URL, runs some logic under the hood, and figures out what type of page the visitor is looking at. That’s a very simplified explanation of it anyway. For theme development, you don’t need to know *how* this part of the process works too deeply—just what the end result is.
 -->

WordPress は、誰かがあなたのサイトのページにアクセスすると、URL を見て、裏でいくつかのロジックを実行し、訪問者が見ているページの種類を把握します。とにかく、これは非常に単純化された説明です。テーマ開発では、プロセスのこの部分が *どのように* 機能するのかを深く知る必要はありません — 最終的な結果がどうなるかを知るだけでいいのです。

<!-- 
Once WordPress determines the type of page, it runs through its “template loader,” which searches for a template that matches the page type. It does this by attempting to locate templates within the template hierarchy for the page type, which is covered in detail in the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/) documentation.
 -->

WordPress はページの種類を決定すると、「テンプレート・ローダ」を実行し、ページの種類に合致するテンプレートを探します。これはページタイプ用のテンプレート階層内でテンプレートを見つけようとすることで行われ、[テンプレート階層](https://developer.wordpress.org/themes/templates/template-hierarchy/) ドキュメントで詳しく説明されています。

<!-- 
WordPress will search for templates in the hierarchy in order of priority. If it finds a match in any of these locations, it will stop searching through the hierarchy:
 -->

WordPress はその優先順位に従って階層内のテンプレートを検索します。これらの場所のいずれかに合致するものがあれば、階層の検索を停止します:

<!-- 
*   User-saved template in the database.
*   Template in a child theme’s `/templates` folder (if child theme is active).
*   Template in the theme’s `/templates` folder.
 -->

*   データベース内のユーザー保存テンプレート。
*   (子テーマが有効化されている場合) 子テーマの `/templates` フォルダー内のテンプレート。
*   テーマの `/templates` フォルダー内のテンプレート。

<!-- 
Once a template is found that matches the page type within the hierarchy, the template is loaded. Its block markup is then parsed and WordPress outputs the resulting HTML markup for the browser to use.
 -->

階層内のページタイプに合致するテンプレートが見つかると、そのテンプレートがロードされます。その後、そのブロック・マークアップが解析され、WordPress はブラウザーが使用できるように結果の HTML マークアップを出力します。

<!-- 
## What’s in a template?
 -->

## テンプレートの中身って ?

<!-- 
Block theme templates are composed entirely of block markup. That’s it. *Really.*
 -->

ブロック・テーマのテンプレートは、ブロック・マークアップだけで構成されています。それだけです。*本当に。*

<!-- 
OK. It’s slightly more nuanced than that. You will generally see these things in block templates:
 -->

OK。少しニュアンスが違います。一般的に、ブロック・テンプレートには、このようなものがあります:

<!-- 
*   Block markup
*   References to template parts
*   References to block patterns
 -->

*   ブロック・マークアップ
*   テンプレート・パーツへの参照
*   ブロック・パターンへの参照

<!-- 
Ultimately, each of those things is still block markup.
 -->

結局のところ、そのどれもがブロック・マークアップであることに変わりはありません。

<!-- 
Here’s a look at the `/templates/404.html` template file, which includes all three things:
 -->

その3つを含む `/templates/404.html` テンプレートを見てみましょう:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
<main class="wp-block-group">
	<!-- wp:pattern {"slug":"twentytwentythree/hidden-404"} /-->
</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

<!-- 
Of course, block templates can be much more complex than that. The point is that block templates must consist entirely of block markup for WordPress to correctly parse the code and output it for the browser.
 -->

もちろん、ブロック・テンプレートはそれよりもはるかに複雑にできます。要は、WordPress がコードを正しく解析してブラウザーに出力するためには、ブロック・テンプレートはすべてブロック・マークアップで構成されていなければならないということです。

<!-- 
For a more in-depth look at the architecture of a block, check out the [Key Concepts](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) documentation in the Block Editor Handbook.
 -->

ブロックのアーキテクチャーをより詳しく見るには、ブロックエディター・ハンドブックの [キー・コンセプト](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) ドキュメントをご覧ください。

<!-- 
## Organizing templates
 -->

## テンプレートの編成

<!-- 
With block themes, there is only one location that you can put block templates: in the theme’s `/templates` folder. It should be structured like this:
 -->

ブロック・テーマでは、ブロック・テンプレートを置くことができる場所は1つだけ: テーマの `/templates` フォルダーです。その構造はこのようになるはずです:

<!-- 
*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `home.html`
    *   `index.html` (required)
    *   `page.html`
    *   `singular.html`
 -->

*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `home.html`
    *   `index.html` (必須)
    *   `page.html`
    *   `singular.html`

<!-- 
The minimum required template file is `index.html`. The existence of this file is how WordPress determines that the theme is a block theme.
 -->

最低限必須のテンプレート・ファイルは `index.html` です。このファイルの存在によって、WordPress はテーマがブロック・テーマであると判断します。

<!-- 
Outside of that, you can include as many or as few templates as you need to achieve your theme design.
 -->

その他に、あなたのテーマ設計を実現するために必要なテンプレートを、いくつでも含めることができます。

<!-- 
Technically, WordPress will also look in the `/block-templates` folder if it exists in your theme. This is for backward compatibility with an older version of WordPress. But it is recommended to always use the `/templates` folder instead.
 -->

技術的には、WordPress はあなたのテーマに `/block-templates` フォルダーが存在する場合、その中も探します。これは WordPress の古いバージョンとの後方互換性のためです。しかし、代わりに `/templates` フォルダーを常に使用することをおすすめします。

<!-- 
## Building templates
 -->

## テンプレートの構築

<!-- 
While you can technically type all of the block markup for your templates in your template files, that is not what the typical experience will be when working with block themes. In most cases, you will be working from a visual interface and migrating your block code to your template files.
 -->

技術的には、すべてのブロック・マークアップをあなたのテンプレート・ファイルにタイプできますが、ブロック・テーマで作業する際には、それは一般的な経験ではありません。ほとんどの場合、ビジュアルなインターフェースから作業し、ブロック・コードをあなたのテンプレート・ファイルに移行します。

<!-- 
To explore working with the visual interface, read the support guides on using the Site and Template Editors:
 -->

ビジュアルなインターフェースでの作業については、サイト・エディターとテンプレート・エディターの使用に関するサポート・ガイドをお読みください:

<!-- 
*   [Site Editor](https://wordpress.org/documentation/article/site-editor/)
*   [Template Editor](https://wordpress.org/documentation/article/template-editor/)
    *   [How to edit templates via the Site Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [How to use the Template Editor via the WordPress Block Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)
 -->

*   [サイト・エディター](https://wordpress.org/documentation/article/site-editor/)
*   [テンプレート・エディター](https://wordpress.org/documentation/article/template-editor/)
    *   [サイト・エディターを介した、テンプレートの編集法](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [WordPress ブロック・エディターを介した、テンプレート・エディターの使用法](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)

<!-- 
### Editing templates
 -->

### テンプレートの編集

<!-- 
To access templates from the WordPress admin, open the **Appearance > Editor** menu in the admin menu. Then click the **Templates** item in the sidebar:
 -->

WordPress の管理画面からテンプレートにアクセスするには、管理メニューの **外観 > エディター** メニューを開きます。次に、サイドバーの **テンプレート** 項目をクリックします:

<!-- 
[![WordPress Templates interface in the Site Editor, which shows the template options on the left and preview panel on the right.](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?ssl=1)
 -->

[![サイト・エディターの WordPress 「テンプレート」インターフェースでは、左側にテンプレート・オプション、右側にプレビュー・パネルが表示される。](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?ssl=1)

<!-- 
This screen lists all of the existing templates for the site, which can come from three locations:
 -->

この画面には、サイトの既存のテンプレートがすべて一覧表示され、そのテンプレートは3つの場所から取得できます:

<!-- 
*   User-created templates saved in the database
*   Templates from the theme’s `/templates` folder
*   Templates dynamically added by plugins
 -->

*   データベースに保存された、ユーザー制作テンプレート
*   テーマの `/templates` フォルダーからのテンプレート
*   プラグインによって動的に追加されるテンプレート

<!-- 
From there, you can make customizations to the existing templates, adjusting blocks to your liking.
 -->

そこから、既存のテンプレートをカスタマイズし、好みに合わせてブロックを調整できます。

<!-- 
Remember that if you save these, they will be stored in the database and will overrule any templates in your theme. If you plan to distribute this theme to others or use it on another site, you must copy the block markup to the matching template in your `/templates` folder as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).
 -->

これらを保存すると、データベースに保存され、あなたのテーマ内のどのテンプレートよりも優先されることを覚えておいてください。このテーマを他の人に配布したり、他のサイトで使用したりする場合は、[テンプレート入門](https://developer.wordpress.org/themes/templates/introduction-to-templates/) で説明したように、ブロック・マークアップをあなたの `/templates` フォルダーの合致するテンプレートにコピーする必要があります。

<!-- 
### Adding new templates
 -->

### 新規テンプレートの追加

<!-- 
You can create a new template by clicking the **Add New Template** (**+** icon next to **Templates** heading). This will create a modal overlay as shown here:
 -->

新規テンプレートを作成するには、**新規テンプレートの追加** ( **テンプレート** 見出しの隣の **+** アイコン) をクリックします。このようにモーダルオーバーレイが作成されます:

<!-- 
[![WordPress Add Template modal overlaid the Site Editor.](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?resize=1600%2C837&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?ssl=1)
 -->

[![WordPress の「テンプレート追加」モーダルがサイト・エディターに重なる。](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?resize=1600%2C837&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?ssl=1)

<!-- 
From there, you will be able to create an entirely custom template (if it doesn’t already exist for editing).
 -->

そこから、(編集用のテンプレートがまだ存在しない場合) まったくのカスタム・テンプレートを作成できます。

<!-- 
Again, any new templates you add via the editor are saved in the database. You must create the template file inside your `/templates` folder and copy the block markup to it if you intend to distribute your theme. Be sure that your template filename matches a valid filename in the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/) (for example, the Home template filename is `home.html`).
 -->

繰り返しますが、エディターを介して追加した新規テンプレートは、いずれもデータベースに保存されます。テーマを配布する場合は、あなたの `/templates` フォルダー内にテンプレート・ファイルを作成し、ブロック・マークアップをコピーする必要があります。あなたのテンプレートのファイル名が [テンプレート階層](https://developer.wordpress.org/themes/templates/template-hierarchy/) の有効なファイル名と合致していることを確認してください (たとえば、「ホーム」テンプレートのファイル名は `home.html` です)。

<!-- 
### Custom templates
 -->

### カスタム・テンプレート

<!-- 
Custom templates are templates that you can assign to individual posts, pages, or entries of a custom post type. They are used for the single post view on the front end of the site.
 -->

カスタム・テンプレートは、カスタム投稿タイプの個々の投稿、ページ、またはエントリーに割り当て可能なテンプレートです。これらはサイトのフロントエンドの個別投稿ビューに使われます。

<!-- 
You or your theme users can select custom templates from the **Template** setting in the **Post/Page** panel in the post editor sidebar:
 -->

あなた、またはあなたのテーマのユーザーは、投稿エディターのサイドバーにある **投稿/ページ** パネルの **テンプレート** 設定からカスタム・テンプレートを選択できます:

<!-- 
[![WordPress post editor with the Template option open in the sidebar. The Blank template option is highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?resize=2048%2C1068&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?ssl=1)
 -->

[![WordPress の投稿エディターで、サイドバーのテンプレート・オプションを開いた状態。空白のテンプレート・オプションがハイライトされている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?resize=2048%2C1068&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?ssl=1)

<!-- 
This can be a powerful feature that lets you create unique designs for specific circumstances. For example, you could add something as simple as a different layout with a contact form or something as complex as a news-magazine layout with multiple post queries and other sections.
 -->

これは、特定の状況に合わせて独自のデザインを作成できる強力な機能です。たとえば、コンタクトフォーム付きの別のレイアウトのようなシンプルなものから、複数の投稿クエリーやその他のセクションを持つニュースマガジンレイアウトのような複雑なものまで追加できます。

<!-- 
When adding a new template from the **Templates** screen, you can also create a custom template. From the **Add Template** overlay, there is an option named **Custom Template**. By clicking it, you will add a new custom template within your site’s database.
 -->

**テンプレート** 画面から新規テンプレートを追加する際、カスタム・テンプレートも作成できます。**テンプレートの追加** オーバーレイに、**カスタム・テンプレート** というオプションがあります。これをクリックすると、あなたのサイトのデータベースに新規カスタム・テンプレートが追加されます。

<!-- 
But to distribute your template with your theme, you must add it to a custom template file in your theme’s `/templates` folder.
 -->

しかし、あなたのテーマとともにあなたのテンプレートを配布するには、あなたのテーマの `/templates` フォルダー内にカスタム・テンプレート・ファイルを追加する必要があります。

<!-- 
The great thing about custom templates is that the filename can be anything you want it to be. Just be sure to avoid using the name of a standard template filename from the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/), so make sure it’s unique.
 -->

カスタム・テンプレートのすばらしい点は、ファイル名を自由に設定できることです。ただし、[テンプレート階層](https://developer.wordpress.org/themes/templates/template-hierarchy/) にある標準テンプレートのファイル名を使わないように注意して、必ず独自の名前にしてください。

<!-- 
Because custom templates can be anything, there are no exact rules on what block markup should be included in them. But if you want to display the post or page content, make sure that you’re using the Post Content block somewhere within it.
 -->

カスタム・テンプレートはどのようなものでもよいので、どのようなブロック・マークアップを含めるべきかについて、厳密なルールはありません。しかし、投稿やページのコンテンツを表示したいのであれば、その中のどこかで「投稿コンテンツ」ブロックを使用していることを確認してください。

<!-- 
The only other rule is that you must register your template via your `theme.json` file. How to do this is covered in the [Custom Templates](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/) documentation under the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.
 -->

その他の唯一のルールは、あなたの `theme.json` ファイルを介してテンプレートを登録する必要があるということです。この方法は、[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) 章の [カスタム・テンプレート](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/) ドキュメントで説明されています。

<!-- 
Originally, custom templates were called “page templates.” This is because the feature only worked for pages in the initial implementation. Eventually, posts and other custom post types could use the feature, so it was rebranded to “custom templates.” But you may see these referred to as page templates in other documentation or on third-party sites.
 -->

もともとカスタム・テンプレートは「ページ・テンプレート」と呼ばれていました。これは、初期の実装ではこの機能がページにしか使えなかったからです。最終的に、投稿やその他のカスタム投稿タイプでもこの機能が使えるようになったため、「カスタム・テンプレート」に改名されました。しかし、他のドキュメントやサードパーティのサイトでは、ページ・テンプレートと呼ばれているのを見かけるかもしれません。