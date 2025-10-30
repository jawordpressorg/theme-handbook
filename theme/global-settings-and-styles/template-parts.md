<!-- 
# Template Parts
 -->

# テンプレート・パーツ

<!-- 
Template parts are small sections (i.e., *parts*) that you can include in top-level templates. Following the DRY (Don’t Repeat Yourself) principle, they are generally used as sections that need to be reused across multiple templates. Instead of writing the code multiple times, you can break it apart into a single file and include it when needed.
 -->

テンプレート・パーツとは、トップレベル・テンプレートに組み込むことができる小さなセクション (つまり *パーツ*) です。DRY (Do not Repeat Yourself。繰り返すな) 原則に従い、通常は複数のテンプレートで再利用が必要なセクションとして使用されます。コードを複数回記述する代わりに、個別ファイルに分割し、必要なときに組み込むことができます。

<!-- 
Because this chapter is focused on `theme.json`, the goal of this document is to explain how to register template parts within the `theme.json` file. You can dive more deeply into templates and template parts within the [Templates chapter](https://developer.wordpress.org/themes/templates/).
 -->

本章では `theme.json` に焦点を当てているため、本ドキュメントの目標は `theme.json` ファイル内でテンプレート・パーツの登録方法を説明することです。テンプレートとテンプレート・パーツの詳細については、[テンプレート章](https://developer.wordpress.org/themes/templates/) でさらに深く学ぶことができます。

<!-- 
In `theme.json`, you can register additional metadata for template parts, such as the title and area the part is assigned to.
 -->

`theme.json` では、テンプレート・パーツに対して、タイトルや割り当てられた領域などの追加メタデータを登録できます。

<!-- 
## Registering template parts
 -->

## テンプレート・パーツの登録

<!-- 
Technically, you can use custom template parts without ever registering them via `theme.json`. But registering them has some distinct advantages:
 -->

技術的には、`theme.json` 経由で登録せずにカスタム・テンプレート・パーツを使用できます。ただし、登録することには、いくつかの明確な利点があります:

<!-- 
*   You can give the part a translatable title that is more appealing in the user interface.
*   You can assign each part to an area, creating a nicer user experience in the Site Editor.
*   It plays more nicely with plugins, style variations, and child themes that may grab, filter, or otherwise use the registered metadata in some way.
 -->

*   UI 上でより訴求力のある、翻訳可能なタイトルをパーツに設定できます。
*   各パーツをエリアに割り当てることができ、サイトエディターでのユーザー・エクスペリエンスを改善できます。
*   プラグイン、スタイル・バリエーション、子テーマなどとの連携がより良好です。これらは登録されたメタデータを取得、フィルタリング、あるいは何らかの形で利用する場合があります。

<!-- 
To register template parts, you must pass an array of objects to the `templateParts` property in `theme.json`. Each object in the array accepts three key/value pairs:
 -->

テンプレート・パーツを登録するには、`theme.json` 内の `templateParts` プロパティにオブジェクトの配列を渡す必要があります。配列内の各オブジェクトは、以下の3つのキー-値ペアを受け付けます:

<!-- 
*   **`area`:** The area that the template part belongs to. The default options are `header`, `footer`, and `uncategorized`. You can also assign it to any custom area.
*   **`name`:** The filename of your template part without the extension.
*   **`title`:** A human-readable title for your template, which may be translated.
 -->

*   **`area`:** テンプレート・パーツが属する領域です。デフォルトの選択肢は `header`、`footer`、`uncategorized` です。任意のカスタム領域にも割り当て可能です。
*   **`name`:** 拡張子を除いた、テンプレート・パーツのファイル名です。
*   **`title`:** 翻訳可能で、人間可読な、テンプレートのタイトルです。

<!-- 
WordPress will look for template parts in the theme’s `/parts` folder. Therefore, if you register a template part with the name of \`example\`, you must also have a `/parts/example.html` file in your theme.
 -->

WordPress は、テーマの `/parts` フォルダー内でテンプレート・パーツを検索します。したがって、\`example\` という名称でテンプレート・パーツを登録する場合、あなたのテーマ内には `/parts/example.html` ファイルも存在している必要があります。

<!-- 
You will learn more about template part areas in the Templates chapter. Also, check out the [Upgrading the site-editing experience with custom template part areas](https://developer.wordpress.org/news/2023/06/upgrading-the-site-editing-experience-with-custom-template-part-areas/) tutorial on the WordPress Developer Blog for an in-depth walkthrough of creating custom areas.
 -->

テンプレート・パーツ領域の詳細については、「テンプレート」の章で説明します。また、カスタム領域の制作についての詳細な手順については、WordPress 開発者ブログの [カスタム・テンプレート・パーツ領域で、サイト編集体験のアップグレード](https://developer.wordpress.org/news/2023/06/upgrading-the-site-editing-experience-with-custom-template-part-areas/) チュートリアルをご覧ください。

<!-- 
### Registering a template part
 -->

### テンプレート・パーツの登録

<!-- 
The two most common template parts that any theme will register are for a site header and footer. This is also why WordPress has the default areas of `header` and `footer`. You are not required to use these parts or areas, but they are pretty much standard sections for nearly all websites.
 -->

どのテーマでも登録される最も一般的な二大テンプレート・パーツは、サイトヘッダーとフッター用です。これが WordPress に `header` と `footer` というデフォルト領域が存在する理由でもあります。これらのパーツや領域の使用は必須ではありませんが、ほぼすべての Web サイトで標準的なセクションとなっています。

<!-- 
For this exercise, let’s register them both. First, add a couple of empty files named `header.html` and `footer.html` in your theme’s `/parts` folder if they do not already exist. You’ll add some block code to them in the next step.
 -->

本演習では、両方を登録しましょう。まず、あなたのテーマの `/parts` フォルダーに、`header.html` と `footer.html` という空ファイルがまだ存在しない場合は、追加してください。次ステップで、これらのファイルにブロックコードを追加します。

<!-- 
Now register those template parts in `theme.json`:
 -->

では、それらのテンプレート・パーツを `theme.json` に登録します:

```json
{
	"version": 2,
	"templateParts": [
		{
			"area": "header",
			"name": "header",
			"title": "Header"
		},
		{
			"area": "footer",
			"name": "footer",
			"title": "Footer"
		}
	]
}
```

<!-- 
It can be confusing when both the `area` and `name` values match. That’s not always the case, but is often how things look when dealing with the header and footer.
 -->

`area` と `name` の両方の値が一致すると、混乱を招くことがあります。常にそうとは限りませんが、ヘッダーとフッターを扱う際にはよく見られる現象です。

<!-- 
Some theme authors prefer to name the `header` and `footer` template parts `site-header` and `site-footer` to better differentiate them. Feel free to do that if it makes more sense to you. Or rename them to anything you want.
 -->

一部のテーマ作者は、`header`・`footer` テンプレート・パーツを `site-header`・`site-footer` と命名し、区別しやすくすることを好みます。ご自身にとってより理にかなう場合は、そのように命名してください。あるいは、お好きな名前に変更してもかまいません。

<!-- 
You are not limited to these two common template parts. You can add as many parts as you need for your theme project.
 -->

これらの一般的な二大テンプレート・パーツに限定されるわけではありません。あなたのテーマプロジェクトに必要なだけ、いくつでもパーツを追加できます。

<!-- 
### Building a template part
 -->

### テンプレート・パーツの構築

<!-- 
All template parts should be placed in your theme’s `/parts` folder (WordPress also recognizes the `/template-parts` folder for backwards compatibility). So you will now be editing the `/parts/header.html` and `/parts/footer.html` files.
 -->

すべてのテンプレート・パーツは、あなたのテーマの `/parts` フォルダーに配置してください (WordPress は下位互換性のため、`/template-parts` フォルダーも認識する)。したがって、編集対象となるのは `/parts/header.html` と `/parts/footer.html` ファイルです。

<!-- 
You will learn more about building custom template parts in the [Templates chapter](https://developer.wordpress.org/themes/templates/). For the purposes of this documentation, just consider the following code snippets as examples that you can customize.
 -->

カスタム・テンプレート・パーツの構築については、[テンプレート章](https://developer.wordpress.org/themes/templates/) で詳しく説明します。このドキュメントの主旨から、以下のコードスニペットは、カスタマイズ可能な例としてとらえてください。

<!-- 
In your `/parts/header.html` file, add this code:
 -->

あなたの `/parts/header.html` ファイルに、次のコードを追加してください:

```markup
<!-- wp:group {"style":{"spacing":{"padding":{"top":"2rem","bottom":"2rem","right":"2rem","left":"2rem"}}},"layout":{"type":"default"}} -->
<div class="wp-block-group" style="padding-top:2rem;padding-right:2rem;padding-bottom:2rem;padding-left:2rem">
	<!-- wp:group {"layout":{"type":"flex","justifyContent":"space-between"}} -->
	<div class="wp-block-group">
		<!-- wp:site-title /-->
		<!-- wp:navigation {"icon":"menu","layout":{"type":"flex","setCascadingProperties":true,"justifyContent":"right"}} /-->
	</div>
	<!-- /wp:group -->
</div>
<!-- /wp:group -->
```

<!-- 
Then add this code to your `/parts/footer.html` file:
 -->

次に、あなたの `/parts/footer.html` ファイルに、このコードを追加してください:

```markup
<!-- wp:group {"style":{"spacing":{"padding":{"top":"2rem","right":"2rem","bottom":"2rem","left":"2rem"}}}} -->
<div class="wp-block-group" style="padding-top:2rem;padding-right:2rem;padding-bottom:2rem;padding-left:2rem">

	<!-- wp:group {"align":"wide","style":{"spacing":{"blockGap":"0"}},"layout":{"type":"flex","orientation":"vertical","justifyContent":"center"}} -->
	<div class="wp-block-group alignwide">
		<!-- wp:site-title {"level":0,"isLink":false,"className":"is-style-normalize"} /-->

		<!-- wp:paragraph -->
			<p>Powered by WordPress.</p>
		<!-- /wp:paragraph -->
	</div>
	<!-- /wp:group -->

</div>
<!-- /wp:group -->
```

<!-- 
Now go to **Appearance > Editor** in your WordPress admin and look at the **Patterns > Template Parts** section. You should see both the **Header** and **Footer** areas listed with your custom template parts:
 -->

では、あなたの WordPress 管理画面で **外観 > エディター** に移動し、**パターン > テンプレート・パーツ** セクションを確認してください。あなたのカスタム・テンプレート・パーツとともに、**ヘッダー** と **フッター** の両方の領域が表示されているはずです:

<!-- 
[![Templates screen in the WordPress Site Editor. The Header area is specifically selected, showing a single Header template part.](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-site-editor.jpg?ssl=1)
 -->

[![WordPress サイトエディターのテンプレート画面。ヘッダー領域が特に選択されており、個別ヘッダー・テンプレート・パーツが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-site-editor.jpg?ssl=1)

<!-- 
### Including a template part
 -->

### テンプレート・パーツの組込み

<!-- 
Creating template part files and registering them in `theme.json` does not mean that your parts will automatically appear on the site. Because they are only *parts*, you must also include them inside of a template.
 -->

テンプレート・パーツ・ファイルを制作し、`theme.json` に登録しても、それだけでパーツがサイトに自動的に表示されるわけではありません。これらはあくまで *パーツ* であるため、テンプレート内に組み込む必要があります。

<!-- 
Remember, you’ll learn more about creating templates in the [Templates documentation](https://developer.wordpress.org/themes/templates/) if you are not already familiar with them. For now, you just need to test how the registration process works.
 -->

テンプレートの制作については、[テンプレート・ドキュメント](https://developer.wordpress.org/themes/templates/) で詳しく学べますので、まだご存じでない場合はそちらをご覧ください。現時点では、登録プロセスがどのように機能するかテストするだけで十分です。

<!-- 
To include a template part in a top-level template, you must use the Template Part block. The basic markup for this block is:
 -->

トップレベル・テンプレートにテンプレート・パーツを組み込むには、「テンプレート・パーツ」ブロックを使用する必要があります。このブロックの基本的なマークアップは、次のとおりです:

```markup
<!-- wp:template-part {"slug":"your-part-slug"} /-->
```

<!-- 
So open one of the template files from your theme’s `/templates` folder. Your theme should at least have an `index.html` template there, but you can test with any file.
 -->

あなたのテーマの `/templates` フォルダーからテンプレート・ファイルを1つ開いてください。あなたのテーマには少なくとも `index.html` テンプレートが存在するはずですが、どのファイルでもテストできます。

<!-- 
Now add the calls to the `wp:template-part` block as shown here:
 -->

では、ここに示すように `wp:template-part` ブロックへのコールを、以下のように追加しましょう:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- Other block markup goes here. -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

<!-- 
Now you should be able to see both the Header and Footer template parts if you open the top-level template you added them to via **Appearance > Editor > Templates** in your WordPress admin:
 -->

では、あなたの WordPress 管理画面で **外観 > エディター > テンプレート** から追加したトップレベル・テンプレートを開くと、ヘッダーとフッターの両方のテンプレート・パーツが表示されるはずです:

<!-- 
[![WordPress Site Editor with a template being edited. The Header template part is selected.](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-include.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-include.jpg?ssl=1)
 -->

[![テンプレートを編集中の WordPress サイトエディター。「ヘッダー」テンプレート・パーツが選択されている。](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-include.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/09/template-parts-include.jpg?ssl=1)