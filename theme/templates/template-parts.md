<!-- 
# Template Parts
 -->

# テンプレート・パーツ

<!-- 
[Templates](https://developer.wordpress.org/themes/templates/templates/) represent the top-level document structure for the front end of a website. But ***template parts*** represent smaller sections of content that can be included in one or more templates.
 -->

[テンプレート](https://developer.wordpress.org/themes/templates/templates/) は、Web サイトのフロントエンドにおける、トップレベルのドキュメント構造を表現しています。一方、***テンプレート・パーツ*** は、1つまたは複数のテンプレートに含めることができる、コンテンツの小さなセクションを表現します。

<!-- 
Some common parts are:
 -->

一般的なパーツとしては、以下のようなものが挙げられます:

<!-- 
*   Header
*   Footer
*   Sidebar
*   Comments
 -->

*   ヘッダー
*   フッター
*   サイドバー
*   コメント

<!-- 
You can have many more parts. These are generally pieces of the design that are reused within multiple top-level templates. Parts are not a requirement for your theme, but they are a nice-to-use feature that lets you better manage your files and code.
 -->

さらに多くのパーツを持つことができます。これらは一般的に、複数のトップレベル・テンプレート内で再利用される、設計の一部です。パーツはあなたのテーマにとって必須ではありませんが、あなたのファイルやコードをより良く管理できる使い勝手の良い機能です。

<!-- 
In [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/), you learned about the basics of template parts. In this document, you’ll gain a deeper understanding of how they work.
 -->

[テンプレート入門](https://developer.wordpress.org/themes/templates/introduction-to-templates/) では、テンプレート・パーツの基本について学びました。このドキュメントでは、そのしくみについて理解が深まるでしょう。

<!-- 
## How do template parts work?
 -->

## テンプレート・パーツのしくみって ?

<!-- 
As you learned in the Templates documentation, WordPress locates a top-level template based on which page a visitor is viewing on the website. This located template is then loaded, and WordPress parses the block markup before sending it back to the browser.
 -->

テンプレートのドキュメントで学んだように、訪問者が Web サイトのどのページを見ているかにもとづいて、WordPress はトップレベルのテンプレートを探します。そして、この探し出されたテンプレートがロードされ、ブロック・マークアップを解析してから、WordPress はブラウザーに送り返します。

<!-- 
Unlike templates, parts are not automatically loaded based on the currently-viewed page. They must be included as a *part* of the top-level template via the [Template Part block](https://wordpress.org/documentation/article/template-part-block/).
 -->

テンプレートとは異なり、パーツは現在の表示ページにもとづいて自動的にロードされることはありません。それらは、[「テンプレート・パーツ」ブロック](https://wordpress.org/documentation/article/template-part-block/) を介して、トップレベル・テンプレートの *部品* として、含まれなければなりません。

<!-- 
The Template Part block’s markup looks like this:
 -->

「テンプレート・パート」ブロックのマークアップは、次のようになります:

```markup
<!-- wp:template-part {"slug":"your-template-part-slug"} /-->
```

<!-- 
There are more block settings that you can include, but the `slug` property **must** be set to load the correct part. When WordPress encounters the Template Part block markup during its parsing process, it will look for a file named `/parts/your-template-part-slug.html` in your theme folder. If found, it will load the file and parse its block markup.
 -->

含めることができるブロック設定は他にもありますが、正しいパーツをロードするために `slug` プロパティは **必ず** 設定しなければなりません。WordPress がその解析処理中にテンプレート・パーツのブロック・マークアップに遭遇すると、あなたのテーマ・フォルダー内で `/parts/your-template-part-slug.html` という名前のファイルを探します。見つかった場合、そのファイルをロードし、ブロック・マークアップを解析します。

<!-- 
Let’s look at a simple template that loads both a Header and Footer part:
 -->

ヘッダー部分とフッター部分の両方をロードする、シンプルなテンプレートを見てみましょう:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- Other block markup goes here. -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

<!-- 
As you can see, a `tagName` setting was also included for the Header and Footer parts. This sets the wrapping container elements to `<header>` and `<footer>`, respectively.
 -->

ご覧のように、ヘッダーとフッター部分には `tagName` 設定も含まれています。これは、ラップするコンテナ要素を `<header>` と `<footer>` それぞれに設定します。

<!-- 
If this is the block markup included in a top-level template, WordPress would go through these steps:
 -->

これがトップレベル・テンプレートに含まれるブロック・マークアップの場合、WordPress は以下のステップを踏むことになります:

<!-- 
1.  Load the `/parts/header.html` file and parse its block markup.
2.  Parse the template’s other block markup.
3.  Load the `/parts/footer.html` file and parse its block markup.
 -->

1.  `/parts/header.html` ファイルをロードし、そのブロック・マークアップを解析する。
2.  テンプレートの他のブロック・マークアップを解析する。
3.  `/parts/footer.html` ファイルをロードし、そのブロック・マークアップを解析する。

<!-- 
## What’s in a template part?
 -->

## テンプレート・パーツの中身って ?

<!-- 
Template parts in block themes contain block markup and nothing else.
 -->

ブロック・テーマのテンプレート・パーツは、ブロック・マークアップを含み、それ以外は何も含みません。

<!-- 
Let’s look at a simple Footer template part that shows a Site Title block and a Paragraph block with a “Powered by WordPress” message. To recreate this, you would add a `/parts/footer.html` file in your theme with this block markup:
 -->

「サイトタイトル」ブロックと「Powered by WordPress」メッセージ付き「段落」ブロックを表示する、シンプルな「フッター」テンプレート・パーツを見てみましょう。これを再作成するには、あなたのテーマに、このブロック・マークアップを含む `/parts/footer.html` ファイルを追加します:

```markup
<!-- wp:group {"align":"wide","layout":{"type":"flex","orientation":"vertical","justifyContent":"center"}} -->
<div class="wp-block-group alignwide">
	<!-- wp:site-title {"level":0} /-->

	<!-- wp:paragraph -->
		<p>Powered by WordPress.</p>
	<!-- /wp:paragraph -->
</div>
<!-- /wp:group -->
```

<!-- 
This is merely an example that shows block markup and how it *could* look in a part. Template parts can be even simpler or much more complex, depending on what you want to include in them.
 -->

これは、パーツの中でブロック・マークアップとそれが *どのように見えるか* を示す単なる例です。テンプレート・パーツは、その中に何を含めるかによって、もっとシンプルにも、もっと複雑にもできます。

<!-- 
For a more in-depth look at the architecture of a block, check out the [Key Concepts](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) documentation in the Block Editor Handbook.
 -->

ブロックのアーキテクチャーをより詳しく見るには、ブロックエディター・ハンドブックの [キーコンセプト](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) ドキュメントをご覧ください。

<!-- 
## Organizing template parts
 -->

## テンプレート・パーツの編成

<!-- 
With block themes, you must put template parts within your theme’s `/parts` folder. It should be structured like this:
 -->

ブロック・テーマでは、あなたのテーマの `/parts` フォルダー内にテンプレート・パーツを置く必要があります。このような構造になっているはずです:

*   `parts/`
    *   `comments.html`
    *   `footer.html`
    *   `header.html`
    *   `sidebar.html`

<!-- 
None of those are required. In fact, you don’t even have to include any template parts at all.  
WordPress does not currently [support nested template parts](https://github.com/WordPress/gutenberg/issues/54279). For example, you cannot create a `/parts/header` folder and put multiple header parts within it. All template parts must be placed directly within your theme’s `/parts` folder.
 -->

どれも必須ではありません。実際、テンプレート・パーツを含める必要はまったくありません。
WordPress は現在のところ、[テンプレート・パーツの入れ子に対応](https://github.com/WordPress/gutenberg/issues/54279) していません。たとえば、`/parts/header` フォルダーを作成して、その中に複数のヘッダー・パーツを入れることはできません。すべてのテンプレート・パーツは、あなたのテーマの `/parts` フォルダー内に直接配置する必要があります。

<!-- 
Technically, WordPress will also look in the `/block-template-parts` folder if it exists in your theme. This is for backward compatibility with an older version of WordPress. But it is recommended to always use the `/parts` folder instead.
 -->

技術的には、あなたのテーマに `/block-template-parts` フォルダーが存在する場合、WordPress はそれも探します。これは WordPress の古いバージョンとの後方互換性のためです。しかし、代わりに `/parts` フォルダーを常に使用することをおすすめします。

<!-- 
## Building template parts
 -->

## テンプレート・パーツの構築

<!-- 
It’s possible to manually write the block markup code for all of your template parts. But, in most cases, you will want to work directly within the WordPress admin and its visual editor. Then, migrate the block markup from the editor to your template part files as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).
 -->

すべてのテンプレート・パーツのブロック・マークアップ・コードを手作業で記述できます。しかし、ほとんどの場合、WordPress の管理画面とそのビジュアルなエディターで直接作業したいでしょう。そして、[テンプレート入門](https://developer.wordpress.org/themes/templates/introduction-to-templates/) で説明したように、エディターからテンプレート・パーツ・ファイルにブロック・マークアップを移行します。

<!-- 
To explore working with the visual interface, read the support guides on using the Site and Template Editors:
 -->

ビジュアル・インターフェースでの作業については、サイト・エディターとテンプレート・エディターの使用に関するサポート・ガイドをご覧ください:

<!-- 
*   [Template Part Block](https://wordpress.org/documentation/article/template-part-block/)
*   [Site Editor](https://wordpress.org/documentation/article/site-editor/)
*   [Template Editor](https://wordpress.org/documentation/article/template-editor/)
    *   [How to edit templates via the Site Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [How to use the Template Editor via the WordPress Block Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)
 -->

*   [「テンプレート・パーツ」ブロック](https://wordpress.org/documentation/article/template-part-block/)
*   [サイト・エディター](https://wordpress.org/documentation/article/site-editor/)
*   [テンプレート・エディター](https://wordpress.org/documentation/article/template-editor/)
    *   [サイト・エディター経由でのテンプレートの編集法](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [WordPress ブロック・エディター経由でのテンプレート・エディターの使用法](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)

<!-- 
### Registering template parts
 -->

### テンプレート・パーツの登録

<!-- 
While not required, you should almost always register template parts via `theme.json`. Doing so will ensure that they appear in the user interface for use with the Site and Template editors with nice labels that can be translated.
 -->

必須ではありませんが、ほとんどの場合、`theme.json` 経由でテンプレート・パーツを登録する必要があります。そうすることで、サイト・エディターやテンプレート・エディターで使用するユーザーインターフェースに、翻訳可能な素敵なラベルとともに表示されます。

<!-- 
Registering template parts is covered in the [Template Parts](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/) documentation under the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.
 -->

テンプレート・パーツの登録については、[グローバル設定とスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/) 章以下の、[テンプレート・パーツ](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/) ドキュメントで説明されています。

<!-- 
### Editing template parts
 -->

### テンプレート・パーツの編集

<!-- 
To access templates from the WordPress admin, open the **Appearance > Editor** menu in the admin menu. Then click the **Patterns** item in the sidebar and scroll to find the **Template Parts** section:
 -->

WordPress 管理画面からテンプレートにアクセスするには、管理画面メニューの **外観 > エディター** を開きます。続いて、サイドバーの **パターン** 項目をクリックし、スクロールして **テンプレート・パーツ** セクションを見つけます:

<!-- 
[![WordPress Template Parts section under the Patterns library in the Site Editor. A Post Meta and Comments part are both shown on the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?ssl=1)
 -->

[![サイト・エディターのパターン・ライブラリ以下の、WordPress テンプレート・パーツ・セクション。Post Meta と Comments のパーツが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?ssl=1)

<!-- 
Template Parts are categorized by template part areas (read “Template part areas” section below for more information). Each area lists the parts that are registered for it (note that **General** is the `uncategorized` area).
 -->

テンプレート・パーツは、テンプレート・パーツ・エリアごとに分類されています (詳細情報は後述の「テンプレート・パーツ・エリア」セクションをご覧あれ)。各エリアには、そのエリアに登録されているパーツがリストアップされています ( **一般** は `uncategorized` エリアであることに注意)。

<!-- 
The template parts shown can come from three locations:
 -->

テンプレート・パーツは、3ヵ所から入手できます:

<!-- 
*   User-created template parts saved in the database (these are stored as posts in the `wp_template_part` post type)
*   Template parts from the theme’s `/parts` folder
*   Template parts dynamically added by plugins
 -->

*   データベースに保存された、ユーザー制作テンプレート・パーツ (これらは `wp_template_part` 投稿タイプに投稿として保存される)
*   テーマの `/parts` フォルダーから取得した、テンプレート・パーツ
*   プラグインによって動的に追加された、テンプレート・パーツ

<!-- 
From this screen, you can make any customizations you want to the parts, adjusting them to fit your vision.
 -->

この画面から、パーツを自由にカスタマイズし、あなたのイメージに合うように調整できます。

<!-- 
Remember that if you save the parts from this screen, they will be stored in the database and will overrule any templates in your theme. If you plan to distribute this theme to others or use it on another site, you must copy the block markup to the matching template in your `/parts` folder as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).
 -->

この画面からパーツを保存すると、それらはデータベースに保存され、あなたのテーマ内のどのテンプレートよりも優先されることを覚えておいてください。このテーマを他の人に配布したり、他のサイトで使用したりする場合は、[テンプレート入門](https://developer.wordpress.org/themes/templates/introduction-to-templates/) で説明したように、ブロック・マークアップをあなたの `/parts` フォルダーの合致するテンプレートにコピーする必要があります。

<!-- 
### Adding new template parts
 -->

### 新規テンプレート・パーツの追加

<!-- 
You can create a new template by clicking the **+** icon next to **Patterns** heading. This will display a dropdown with several options. Click the **Create template part** option as shown here:
 -->

**パターン** 見出しの隣にある **+** アイコンをクリックして、新規テンプレートを制作できます。いくつかのオプションがドロップダウンメニューに表示されます。ここに示すように、**テンプレート・パーツを追加** オプションをクリックしてください:

<!-- 
[![WordPress Patterns library. A dropdown is shown with the Create Template Part option highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?ssl=1)
 -->

[![WordPress パターン・ライブラリ。ドロップダウンが表示され、「テンプレート・パーツを追加」オプションがハイライトされている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?ssl=1)

<!-- 
Then a popup modal will appear for you to enter a custom template part name and select its area:
 -->

次に、カスタム・テンプレート・パーツ名を入力し、そのエリアを選択するためのポップアップ・モーダルが表示されます:

<!-- 
[![WordPress Site Editor with a modal for creating a template part overlaying the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?ssl=1)
 -->

[![WordPress サイト・エディターに、テンプレート・パーツを制作するためのモーダルがオーバーレイ表示される。](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?ssl=1)

<!-- 
By default, you can select from the General, Header, and Footer areas (to learn more about creating custom areas, read the “Template part areas” section below).
 -->

デフォルトでは、「一般」、「ヘッダー」、「フッター」の各エリアから選択できます (カスタムエリアの制作については、後述の「テンプレート・パーツ・エリア」セクションをご覧あれ)。

<!-- 
From the next screen, you will be able to create an entirely custom template part. It can include any blocks that you prefer.
 -->

次の画面では、完全にカスタム化されたテンプレート・パーツを制作できます。お好きなブロックを含めることができます。

<!-- 
Again, any new parts you add via the editor are saved in the database. You must create the template part file inside your `/parts` folder and copy the block markup to it if you intend to distribute your theme.
 -->

繰り返しますが、エディター経由で追加した新しいパーツは、データベースに保存されます。あなたのテーマを配布するつもりであれば、`/parts` フォルダー内にテンプレート・パーツ・ファイルを作成し、ブロック・マークアップをコピーする必要があります。

<!-- 
## Template part areas
 -->

## テンプレート・パーツ・エリア

<!-- 
Template part areas are essentially a way to organize similar template parts. They also appear as navigational elements within the user interface. Below, you can see the **Header** area highlighted in the template-editing sidebar:
 -->

テンプレート・パーツ・エリアは、基本的に類似したテンプレート・パーツを編成するためのものです。また、これらはユーザーインターフェースのナビゲーション要素としても表示されます。下図は、テンプレート編集サイドバーでハイライトされた **ヘッダー** エリアです:

<!-- 
[![WordPress site editor showing a template with a three-column grid of posts. In the sidebar, the Header area is selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?ssl=1)
 -->

[![WordPress サイト・エディターで、投稿の3列グリッドのテンプレートを表示。サイドバーでは、ヘッダー領域が選択されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?ssl=1)

<!-- 
By default, WordPress has three areas that you can register your templates for:
 -->

デフォルトでは、WordPress には、あなたのテンプレートを登録できる3つのエリアがあります:

<!-- 
*   `uncategorized` (labeled as **General** in the admin)
*   `header`
*   `footer`
 -->

*   `uncategorized` (管理画面で **一般** とラベル付けされる)
*   `header`
*   `footer`

<!-- 
That will cover some common use cases (almost all themes need a header and footer, for example). But you may want to create custom areas for your themes to better organize your template parts and provide a nicer user experience.
 -->

これは、いくつかの一般的なユースケースをカバーします (たとえば、ほとんどすべてのテーマがヘッダーとフッターを必要とする)。しかし、あなたのテンプレート・パーツをよりよく編成し、より良いユーザー体験を提供するために、あなたのテーマ用のカスタム・エリアを制作したいと思うかもしれません。

<!-- 
### Registering custom areas
 -->

### カスタム・エリアの登録

<!-- 
You can register as many custom areas you want by adding a filter to the [`default_wp_template_part_areas` hook](https://developer.wordpress.org/reference/hooks/default_wp_template_part_areas/). Your callback function accepts a single parameter of `$areas`, which must be an array of area definitions. Each area definition must be an array with these key/value pairs defined:
 -->

[`default_wp_template_part_areas` フック](https://developer.wordpress.org/reference/hooks/default_wp_template_part_areas/) にフィルターを追加することで、カスタム・エリアをいくつでも登録できます。あなたのコールバック関数は、エリア定義の配列である `$areas` を単一のパラメータとして受け取ります。各エリア定義は、これらのキー・値のペアが定義された配列でなければなりません:

<!-- 
*   **`area`:** The machine-readable slug for your template part area.
*   **`area_tag`:** The wrapping HTML tag to use for template parts assigned to this area. Can be one of the following:
    *   `div`
    *   `article`
    *   `aside`
    *   `footer`
    *   `header`
    *   `main`
    *   `section`
*   **`label`:** A human-readable label for your area, which may be translated.
*   **`description`:** A description of your area and what template parts belong to it, which may be translated.
*   **`icon`:** The icon to use for the area. Note that only `header`, `footer`, and `sidebar` are currently supported with everything else falling back to a default icon, at least until [this ticket is addressed](https://github.com/WordPress/gutenberg/issues/36814).
 -->

*   **`area`:** テンプレート・パーツ・エリアの、機械可読スラッグです。
*   **`area_tag`:** このエリアに割り当てられたテンプレート・パーツ用に使用される、ラッピング HTML タグです。以下のいずれかを指定します:
    *   `div`
    *   `article`
    *   `aside`
    *   `footer`
    *   `header`
    *   `main`
    *   `section`
*   **`label`:** 翻訳されることもある、あなたのエリア用の可読ラベルです。
*   **`description`:** 翻訳されることもある、あなたのエリアと、それに属するテンプレート・パーツの説明です。
*   **`icon`:** エリア用に使用するアイコンです。現在のところ、`header`、`footer`、`sidebar` のみが対応し、それ以外は、[このチケットに対処](https://github.com/WordPress/gutenberg/issues/36814) するまでは、少なくとも、デフォルトのアイコンにフォールバックすることに注意してください。

<!-- 
Suppose you wanted to create an area named Loop to assign template parts used throughout your theme. You could do so by adding this code to your theme’s `functions.php` file:
 -->

あなたのテーマ全体で使用されるテンプレート・パーツを割り当てるために、Loop という名前のエリアを制作したいとします。あなたのテーマの `functions.php` ファイルに次のコードを追加すれば、できます:

```php
add_filter( 'default_wp_template_part_areas', 'themeslug_template_part_areas' );

function themeslug_template_part_areas( array $areas ) {
	$areas[] = array(
		'area'        => 'loop',
		'area_tag'    => 'section',
		'label'       => __( 'Loop', 'themeslug' ),
		'description' => __( 'Custom description', 'themslug' ),
		'icon'        => 'layout'
	);

	return $areas;
}
```

<!-- 
This would register a new Loop area for your theme, but for it to be useful, you need to also register at least one template part for it as described in the [`theme.json` documentation on registering template parts](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/).
 -->

これは、あなたのテーマに新規 Loop エリアを登録しますが、これを有効にするには、[テンプレート・パーツの登録に関する `theme.json` ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/) で説明されているように、少なくとも1つのテンプレート・パーツも登録する必要があります。

<!-- 
Suppose you also created a `/parts/loop-default.html` template part. You could assign it to your new `loop` area in `theme.json` with this code:
 -->

`/parts/loop-default.html` テンプレート・パーツも作成したとします。このコードで、`theme.json` のあなたの新規 `loop` エリアにそれを割り当てできます:

```json
{
	"version": 2,
	"templateParts": [
		{
			"area": "loop",
			"name": "loop-default",
			"title": "Loop - Default"
		}
	]
}
```

<!-- 
This screenshot shows what the **Loop** area would look like in the Site Editor:
 -->

このスクリーンショットは、サイト・エディターで **Loop** エリアがどのように見えるかを示しています:

<!-- 
[![Template Parts section in the Patterns library in the WordPress Site Editor. A custom Loop template part area is selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?ssl=1)
 -->

[![WordPress サイト・エディターの、パターン・ライブラリ以下のテンプレート・パーツ・セクション。カスタム「Loop」テンプレート・パーツ・エリアが選択されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?ssl=1)

<!-- 
You can register as many template parts for an area as you need via `theme.json`. For example, you could register a `loop-home.html` and `loop-author.html` to use in your Home and Author templates, respectively. But these are mere examples. The only limit is your imagination.
 -->

`theme.json` を介して、1つのエリアに必要な数のテンプレート・パーツを登録できます。たとえば、`loop-home.html` と `loop-author.html` をあなたの Home テンプレートと Author テンプレートにそれぞれ登録できます。しかし、これらは単なる例です。あなたの想像力だけが唯一の限界です。

<!-- 
There are many reasons you might want to register custom areas. For a deeper dive into the benefits and features of this system, read [Upgrading the site-editing experience with custom template part areas](https://developer.wordpress.org/news/2023/06/upgrading-the-site-editing-experience-with-custom-template-part-areas/) from the WordPress Developer Blog.
 -->

カスタムエリアを登録したい理由は、たくさんあるでしょう。このシステムの利点と特長についてより深く知りたい人は、WordPress 開発者ブログの [カスタム・テンプレート・パーツ・エリアでのサイト編集体験のアップグレード](https://developer.wordpress.org/news/2023/06/upgrading-the-site-editing-experience-with-custom-template-part-areas/) をご覧ください。