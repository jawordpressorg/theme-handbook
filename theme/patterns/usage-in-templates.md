<!-- 
# Usage in Templates
 -->

# テンプレートでの使用法

<!-- 
When building themes, patterns are not merely reusable sections of blocks that users can add to their content. That is a nice feature, but the true power of patterns is using them directly in your theme’s front-end output.
 -->

テーマを構築する際、パターンは単にユーザーがコンテンツに追加できる再利用可能なブロックのセクションではありません。これは便利な機能ですが、パターンの真の力は、あなたのテーマのフロントエンド出力に直接使用することにあります。

<!-- 
In this article, you will learn both why and how to include patterns in your theme’s templates and template parts.
 -->

本記事では、あなたのテーマのテンプレートおよびテンプレート・パーツに、パターンを組み込む理由と方法について学びます。

<!-- 
## Why use patterns in templates?
 -->

## テンプレートでパターンを使用する理由って ?

<!-- 
There are two primary reasons to use patterns in your templates:
 -->

あなたのテンプレートにパターンを使用する主な理由は、2つあります:

<!-- 
*   **PHP access:** Block templates and template parts are HTML files and you need access to various PHP functions for dynamic functionality. You can learn more about this in the [Using PHP in Patterns](https://developer.wordpress.org/themes/patterns/using-php-in-patterns/) documentation.
*   **The DRY (Don’t Repeat Yourself) principle:** When building any type of software (themes included) you should always reuse code when possible, which means less work for you and fewer potential bugs. Because patterns are reusable groups of blocks, it makes sense to use the pattern instead of rewriting the code in your templates and parts.
 -->

*   **PHP アクセス:** ブロック・テンプレートとテンプレート・パーツは HTML ファイルであり、動的な機能を実現するために、さまざまな PHP 関数へのアクセスが必要です。これに関する詳細は、[パターンで PHP の利用](https://developer.wordpress.org/themes/patterns/using-php-in-patterns/) ドキュメントを御覧ください。
*   **DRY (Don't Repeat Yourself。繰り返しを避ける) 原則:** あらゆる種類のソフトウェア (テーマを含む) を構築する際は、可能な限りコードを再利用すべきで、これにより、作業量が減り、潜在的なバグも減少します。パターンは再利用可能なブロックの集合体であるため、あなたのテンプレートやパーツでコードを再記述する代わりに、パターンを使用するほうが理にかなっています。

<!-- 
This article will primarily focus on the last point. You will learn how to reuse your patterns within your theme’s block templates and template parts.
 -->

本記事では、主に最後のポイントに焦点を当てます。あなたのテーマのブロック・テンプレートやテンプレート・パーツ内で、あなたのパターンを再利用する方法について学びます。

<!-- 
One of the best use cases is to create patterns of common elements across multiple templates. For example, if your Home, Archive, and Search templates all include the same Query Loop layout, create a pattern for that design and include it in each template.
 -->

最も有用なユースケースの一つは、複数のテンプレートに跨る共通要素のパターンを制作することです。たとえば、あなたの「ホーム」、「アーカイブ」、「検索」テンプレートがすべて同じ「クエリー・ループ」レイアウトを含んでいる場合、その設計用のパターンを制作し、各テンプレートに組み込みます。

<!-- 
## The Pattern block
 -->

## 「パターン」ブロック

<!-- 
As described in [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/), a block pattern is merely one or more blocks that you have registered as a pattern. However, there is also a block named Pattern available in WordPress. You won’t find the Pattern block anywhere in the UI (such as the block inserter). It’s primarily meant to be used in WordPress themes.
 -->

[パターン入門](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/) で説明されているように、ブロック・パターンとは、パターンとして登録した1つまたは複数のブロックのことです。ただし、WordPress には「パターン」という名前のブロックも存在します。この「パターン」ブロックは、(ブロック・インサーターなど) UI のどこにも表示されません。主に WordPress テーマで使用するためのものです。

<!-- 
Here is what the Pattern block markup looks like:
 -->

「パターン」ブロック ・マークアップは、次のようなものです:

```markup
<!-- wp:pattern {"slug":"namespace/pattern-slug"} /-->
```

<!-- 
As you can see, it looks just like any other block markup. The big difference is that you must set the `slug` parameter to include a specific pattern. The value must include both the pattern namespace and slug.
 -->

ご覧の通り、他のブロック・マークアップとまったく同じように見えます。大きな違いは、特定のパターンを含めるために `slug` パラメータを設定する必要がある点です。値には、パターンの名前空間とスラッグの両方を含める必要があります。

<!-- 
Whenever you want to include a pattern within a template or template part, you only need to call the Pattern block.
 -->

テンプレートまたはテンプレート・パーツ内にパターンを含めたい場合は、「パターン」ブロックを呼び出すだけです。

<!-- 
You can also include patterns registered by WordPress or plugins in templates, not just those from your theme. All you need to do is reference the correct `slug` value when calling the Pattern block.
 -->

あなたのテーマのパターンだけでなく、WordPress で登録されているパターンや、テンプレート内のプラグインで登録されているパターンも、含めることができます。「パターン」ブロックをコールする際に、正しい `slug` 値を参照するだけで済みます。

<!-- 
## Adding a pattern to a template
 -->

## テンプレートにパターンの追加

<!-- 
In this section, you will walk through a practical example of including a pattern within a template.
 -->

本セクションでは、テンプレート内にパターンを含める、実践的な例を解説します。

<!-- 
Assume you had a “hero” pattern that you have registered for your theme because you want users to be able to insert it anywhere they need to. But you also want to include this in your Home template by default.
 -->

ユーザーがどこにでも挿入できるように、あなたのテーマに「ヒーロー」パターンを登録したと仮定しましょう。しかし、あなたはこれをデフォルトで「ホーム」テンプレートにも含めたいと考えています。

<!-- 
First, register a custom pattern with the `themeslug/hero`, as described in the [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) documentation. Create a new file named `hero.php` and place it into your theme’s `/patterns` folder with this code:
 -->

まず、[パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) ドキュメントに記載されているように、`themeslug/hero` にカスタム・パターンを登録します。あなたのテーマの `/patterns` フォルダーに `hero.php` という名前の新規ファイルを作成し、以下のコードを記述します:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","isUserOverlayColor":true,"align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themeslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
This will make the pattern both available to users via the UI and to your theme templates for inclusion.
 -->

これにより、パターンはユーザーが UI 経由で利用できるようになり、あなたのテーマ・テンプレートにも組み込むことが可能になります。

<!-- 
To include this specific pattern in a template, you need to call it like so:
 -->

この特定のパターンをテンプレートに含めるには、次のように呼び出します:

```markup
<!-- wp:pattern {"slug":"themeslug/hero"} /-->
```

<!-- 
Now try adding it to one of your theme’s templates, such as `/templates/home.html` or `/templates/index.html` below the header. Your template with the pattern code should look similar to this:
 -->

では、あなたのテーマ・テンプレートの一つ、たとえば、ヘッダー以下にある `/templates/home.html` または `/templates/index.html` に、このコードを追加してみましょう。パターン・コードを含むあなたのテンプレートは、次のような見た目になるはずです:

```markup
<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:pattern {"slug":"themeslug/hero"} /-->

<!-- Some other blocks. /-->

<!-- wp:template-part {"slug":"footer"} /-->
```

<!-- 
Now test the addition of the pattern in the Site Editor by going to **Appearance > Editor > Templates** and choosing the template you added it to:
 -->

次に、**外観 > エディター > テンプレート** に移動し、追加したテンプレートを選択することで、サイト・エディターでパターンの追加をテストします:

<!-- 
[![WordPress Site Editor with the Home/Blog template open. It shows a Header template part and a "welcome" message in a Cover block at the top of the template.](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?ssl=1)
 -->

[![WordPress サイト・エディターで、「ホーム/ブログ」テンプレートが開かれている。テンプレートの最上部に、ヘッダーのテンプレート・パーツと「カバー」ブロック内に「ようこそ」というメッセージが表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?ssl=1)

<!-- 
The pattern should also appear on the front end of your site when that template is in use.
 -->

そのテンプレートが使用されている場合、そのパターンはサイトのフロントエンドにも表示される必要があります。

<!-- 
From this point, you can use this feature however you need. Whether you’re including a pattern in a template or template part, the process is the same.
 -->

この時点で、必要に応じてこの機能をご利用いただけます。テンプレートやテンプレート・パーツとして、パターンを含める場合でも、手順は同じです。