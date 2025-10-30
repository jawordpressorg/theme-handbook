<!-- 
# Custom Templates
 -->

# カスタム・テンプレート

<!-- 
WordPress lets you register custom templates in `theme.json`. More specifically, you can register single post, page, or CPT (custom post type) templates via the `customTemplates` property.
 -->

WordPress では、`theme.json` にカスタム・テンプレートを登録できます。具体的には、`customTemplates` プロパティを通じて、個別投稿、ページ、または CPT (カスタム投稿タイプ) のテンプレートを登録できます。

<!-- 
It’s important to make the distinction that these templates are meant for single post/page/CPT templates and not for other types of templates. When registering these templates, your theme users can select them from the edit post screen, and their post’s design will match the template on the front end of the site.
 -->

これらのテンプレートは、個別投稿/ページ/カスタム投稿タイプのテンプレート向けに設計されており、他の種類のテンプレートには適用されない点に注意が必要です。これらのテンプレートを登録すると、あなたのテーマのユーザーは投稿の編集画面からそれらを選択でき、投稿のデザインは、サイトのフロントエンドでテンプレートに一致します。

<!-- 
Custom templates give you a lot of flexibility in designing variations on your default post or page templates. For example, you could create a blank post template that only shows the content, design a page template with a sidebar, or even one that has no sidebars at all. Really, it depends on what your goals are for your theme project.
 -->

カスタム・テンプレートを使用すると、あなたのデフォルトの投稿やページ・テンプレートのバリエーションを設計する際に、非常に柔軟に対応できます。たとえば、コンテンツのみを表示する空白の投稿テンプレートを作成したり、サイドバー付きのページ・テンプレートをデザインしたり、あるいはサイドバーをまったく持たないテンプレートも作成できます。実際のところ、あなたのテーマプロジェクトの目標が何であるかによって異なります。

<!-- 
This documentation is to teach you how to register custom templates via `theme.json`. For a more extensive look into how to build custom templates, check out the [Templates documentation](https://developer.wordpress.org/themes/templates/).
 -->

本ドキュメントは、`theme.json` を介してカスタム・テンプレートの登録方法を解説するものです。カスタム・テンプレートの構築方法についてより詳細な情報が必要な場合は、[テンプレートのドキュメント](https://developer.wordpress.org/themes/templates/) をご覧ください。

<!-- 
## Adding custom templates
 -->

## カスタム・テンプレートの追加

<!-- 
You can register custom templates via the `customTemplates` property in `theme.json`. It accepts an array of template objects, each defining an individual template.
 -->

カスタム・テンプレートは、`theme.json` 内の `customTemplates` プロパティ経由で登録できます。このプロパティは、テンプレート・オブジェクトの配列を受け付け、各オブジェクトが個別のテンプレートを定義します。

<!-- 
Each object passed to the `customTemplates` array supports these properties:
 -->

`customTemplates` 配列に渡される各オブジェクトは、以下のプロパティをサポートします:

<!-- 
*   **`name`:** The name of your template file without the file extension.
*   **`title`:** A human-readable title for your template, which may be translated.
*   **`postTypes`:** An array of post type slugs that the template is usable on. This is an optional setting and defaults to the `page` post type.
 -->

*   **`name`:** ファイル拡張子を除いた、あなたのテンプレート・ファイルの名称です。
*   **`title`:** 翻訳可能な、あなたのテンプレートの人間可読タイトルです。
*   **`postTypes`:** テンプレートが使用可能な、投稿タイプのスラッグの配列です。これは任意設定であり、デフォルトでは投稿タイプ `page` となります。

<!-- 
For block themes, WordPress will look for custom templates (all templates, actually) in the theme’s `/templates` folder. Therefore, if you register a template with the name of `example`, you must also have an `/templates/example.html` file in your theme.
 -->

ブロック・テーマの場合、WordPress はテーマの `/templates` フォルダー内でカスタム・テンプレート (実際にはすべてのテンプレート) を探します。したがって、`example` という名前のテンプレートを登録する場合、あなたのテーマ内に `/templates/example.html` ファイルも存在している必要があります。

<!-- 
You can add as many custom templates as you want to your theme. Just keep in mind the usability aspect of offering too many choices.
 -->

あなたのテーマには、好きなだけカスタム・テンプレートを追加できます。ただし、選択肢が多すぎると、使い勝手が悪くなる可能性がある点にご注意ください。

<!-- 
### Registering a template
 -->

### テンプレートの登録

<!-- 
Suppose you wanted to create a template named Content Canvas for both pages and posts. This template will only show the site header, post/page content, and site footer. Your users can select it when they need the full content area to behave as a sort of blank canvas.
 -->

ページと投稿の両方に「コンテンツ・キャンバス」という名称のテンプレートを作成したいとしましょう。このテンプレートでは、サイトのヘッダー、投稿/ページのコンテンツ、サイトのフッターのみが表示されます。あなたのテーマのユーザーは、コンテンツ領域全体を一種の白紙のキャンバスのように扱いたい場合に、このテンプレートを選択できます。

<!-- 
The first step you’d take is to create a `/templates/content-canvas.html` file in your theme. Don’t worry about adding anything to it yet; just leave it empty for the moment.
 -->

最初のステップとして、あなたのテーマ内に `/templates/content-canvas.html` ファイルを作成します。現時点では何も追加する必要はありません; とりあえず空のままにしておいてください。

<!-- 
Now register this template in `theme.json`, as shown below:
 -->

次に、以下に示すように、このテンプレートを `theme.json` に登録してください:

```json
{
	"version": 2,
	"customTemplates": [
		{
			"name": "content-canvas",
			"title": "Content Canvas",
			"postTypes": [
				"page",
				"post"
			]
		}
	]
}
```

<!-- 
If you edit a post or page in the WordPress admin, you should see the new **Content Canvas** option under the **Template** selector in the **Post/Page** sidebar panel:
 -->

WordPress 管理画面で投稿やページを編集する場合、**投稿** サイドバーパネルの **テンプレート** セレクタ下に、新規 **Content Canvas** オプションが表示されるはずです:

<!-- 
[![WordPress post editor with the Template select control highlighted in the right sidebar.](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-select.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-select.jpg?ssl=1)
 -->

[![右サイドバーにテンプレート選択コントロールが強調表示された、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-select.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-select.jpg?ssl=1)

<!-- 
### Building a template
 -->

### テンプレートの構築

<!-- 
Now let’s take care of actually building the template, at least for the sake of demonstration. Remember, you can learn more about building templates in the [Templates chapter](https://developer.wordpress.org/themes/templates/) of the handbook.
 -->

それでは、少なくともデモンストレーションのために、実際にテンプレートを作成してみましょう。テンプレートの構築については、ハンドブックの [テンプレート章](https://developer.wordpress.org/themes/templates/) でさらに詳しく学べます。

<!-- 
Add this code to your `/templates/content-canvas.html` file:
 -->

あなたの `/templates/content-canvas.html` ファイルに、このコードを追加してください:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- wp:group {"tagName":"main","layout":{"type":"default"}} -->
<main class="wp-block-group">
	<!-- wp:post-content {"layout":{"type":"constrained"}} /-->
</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

<!-- 
This will give you a working template with an open content area.
 -->

これで、コンテンツ領域が開いた状態の、稼働可能なテンプレートが得られます。

<!-- 
To see what this looks like in the site editor, head over to **Appearance > Editor** in the WordPress admin. Then, select **Content Canvas** under the **Templates** section:
 -->

サイトエディターでこれがどのように表示されるか確認するには、WordPress 管理画面の **外観 > エディター** に移動してください。次に、**テンプレート** セクションで **Content Canvas** を選択します:

<!-- 
[![WordPress Site Editor showing the Content Canvas template on the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-site-editor.jpg?ssl=1)
 -->

[![画面に「Content Canvas」テンプレートを表示している、WordPress サイトエディター。](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/custom-templates-canvas-site-editor.jpg?ssl=1)

<!-- 
This is just a demonstration of what is possible. The real power of custom templates is in what you build with them.
 -->

これは、実現可能なことの単なるデモンストレーションに過ぎません。カスタム・テンプレートの真の力は、それらを使って構築するものにあります。