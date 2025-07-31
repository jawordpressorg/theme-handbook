<!-- 
# Block Type Patterns
 -->

# ブロック・タイプ・パターン

<!-- 
One of the most useful capabilities of patterns is the ability to tie them directly to one or more block types. For example, you can assign a gallery pattern to the Gallery (`core/gallery`) block type and use that specific pattern whenever you insert a new Gallery.
 -->

パターンの最も有用な機能の一つは、それらを1つまたは複数のブロック・タイプに、直接関連付けることができる点です。たとえば、ギャラリー・パターンを「ギャラリー」(`core/gallery`) ブロック・タイプに割り当てると、新規「ギャラリー」を挿入するたびに、その特定のパターンを使用できます。

<!-- 
But the feature offers even more than that. In this article, you will learn how to add a basic connection between a block type and a pattern and how to take advantage of some special cases in WordPress.
 -->

しかし、この機能にはそれ以上の魅力があります。本記事では、WordPress において、ブロック・タイプとパターン間の基本的な関連付けを追加する方法と、いくつかの特殊なケースの利点を取得する方法について説明します。

<!-- 
Besides the techniques described below, block type patterns are also needed for creating starter page patterns, which you can learn more about in the [Starter Patterns](https://developer.wordpress.org/themes/patterns/starter-patterns/) documentation.
 -->

以下に説明される技術に加え、ブロック・タイプ・パターンは、スターター・ページパターンを作成するためにも必要で、詳細については、[「スターター」パターン](https://developer.wordpress.org/themes/patterns/starter-patterns/) ドキュメントをご覧ください。

<!-- 
## Block-specific patterns
 -->

## ブロック固有パターン

<!-- 
It’s important to note that patterns that are connected to a block type behave just like other patterns. What you’re doing is making WordPress aware that the pattern is meant for one or more block types.
 -->

ブロック・タイプに関連付けられたパターンは、他のパターンとまったく同じように動作することに注意してください。あなたがしていることは、そのパターンが1つ以上のブロック・タイプ用であることを WordPress に認識させることです。

<!-- 
For many cases, you may simply want to create a pattern that serves as a starting point when inserting a specific block, and that’s where block type patterns are often useful.
 -->

多くの場合、特定ブロックを挿入する際の出発点として機能するパターンを、作成したいだけかもしれませんが、その際に、ブロック・タイプ・パターンが役立つことはよくあります。

<!-- 
### Register a block type pattern
 -->

### ブロック・タイプ・パターンの登録

<!-- 
As described in [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/), you must assign a value to the `Block Types` header field in your pattern file. This field can accept one or more comma-separated block types, which must include the block’s namespace and slug (e.g., `namespace/slug`).
 -->

[パターンの登録](https://developer.wordpress.org/themes/patterns/registering-patterns/) で説明されているように、あなたのパターン・ファイルの `Block Types` ヘッダー・フィールドに値を割り当てる必要があります。このフィールドには、カンマ区切りでブロック・タイプを1つ以上指定でき、ブロックの名前空間とスラッグ (例: `namespace/slug`) を含める必要があります。

<!-- 
Here is what the file header of pattern tied to the Cover block might look like:
 -->

以下は、「カバー」ブロックに紐付いたパターンの、ファイル・ヘッダー例です:

```php
<?php
/**
 * Title: Cover With Contrast Background
 * Slug: themeslug/cover-contrast
 * Categories: banner
 * Block Types: core/cover
 * Viewport Width: 1376
 */
?>
```

<!-- 
### Build a block type pattern
 -->

### ブロック・タイプ・パターンの構築

<!-- 
Let’s take what you’ve learned so far and create a pattern for a specific block. In this example, you will create a simple Cover block with a single nested Heading and a background with the `contrast` [color preset](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/).
 -->

これまで学んだことを活用して、特定ブロック用のパターンを制作してみましょう。この例では、単一のネストされた「見出し」と、`contrast` [カラー・プリセット](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/) を使用した背景を持つシンプルな「カバー」ブロックを制作します。

<!-- 
Create a new file named `cover-contrast.php` in your theme’s `/patterns` folder and paste this code inside it:
 -->

あなたのテーマの `/patterns` フォルダー内に `cover-contrast.php` という名前の新規ファイルを作成し、その中に以下のコードをペーストします:

```php
<?php
/**
 * Title: Cover With Contrast Background
 * Slug: themeslug/cover-contrast
 * Categories: banner
 * Block Types: core/cover
 * Viewport Width: 1376
 */
?>
<!-- wp:cover {"overlayColor":"contrast","isUserOverlayColor":true,"align":"full","style":{"elements":{"link":{"color":{"text":"var:preset|color|base"}}}},"textColor":"base","layout":{"type":"constrained"}} -->
<div class="wp-block-cover alignfull has-base-color has-text-color has-link-color">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span>
	<div class="wp-block-cover__inner-container">
		<!-- wp:heading {"textAlign":"center"} -->
			<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'A simple heading', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->
	</div>
</div>
<!-- /wp:cover -->
```

<!-- 
Once you’ve saved your pattern file, it should appear as normal in the inserter and Pattern Library. But the most important thing is to check that it’s working as a block type pattern.
 -->

あなたのパターン・ファイルを保存すると、インサーターと「パターン・ライブラリ」に通常通り表示されるはずです。しかし、最も重要なのは、それがブロック・タイプ・パターンとして正常に機能していることを確認することです。

<!-- 
Open a new post or page in your WordPress admin and insert a Cover block but don’t make any change to it. Then, click the Cover block’s icon in the toolbar. You should see a **Patterns** menu item, and if you click that, your new pattern will appear:
 -->

WordPress 管理画面で新規投稿または新規ページを開き、「カバー」ブロックを挿入して、そのまま変更は加えないでください。続いて、ツールバーの「カバー」ブロックのアイコンをクリックします。**パターン** メニュー項目が表示されるので、それをクリックすると、新規パターンが次のように表示されます:

<!-- 
[![Initial insertion of the Cover block in the block editor. The block's icon is selected in the toolbar and shows a dropdown. In the dropdown, the Patterns sub-menu is selected and shows a transformation option for choosing a pattern.](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-transform.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-transform.webp?ssl=1)
 -->

[![ブロック・エディターでの「カバー」ブロックの初期挿入。ツールバーでブロックのアイコンを選択すると、ドロップダウンが表示される。ドロップダウンで「パターン」サブメニューを選択すると、パターンを選択するための変換オプションが表示される。](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-transform.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-transform.webp?ssl=1)

<!-- 
From there, if you select the pattern that you’ve registered, it will transform your inserted Cover block inside the content area:
 -->

そこから、登録したパターンを選択すると、コンテンツ・エリア内に挿入した「カバー」ブロックが変形します:

<!-- 
[![WordPress post editor with a Cover block inserted into the content area with a single Heading block nested inside it.](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-replaced.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-replaced.webp?ssl=1)
 -->

[![コンテンツ・エリアに「カバー」ブロックが挿入され、その中に1つの「見出し」ブロックがネストされている、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-replaced.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/cover-pattern-replaced.webp?ssl=1)

<!-- 
And that is the basics of how block type patterns work. But WordPress has some special handling for some blocks, which you will learn about below.
 -->

以上が、ブロック・タイプ・パターンの基本的なしくみです。ただし、WordPress では一部のブロックについて特別な処理が行われており、その詳細については、以下で説明します。

<!-- 
## Query Loop patterns
 -->

## 「クエリー・ループ」パターン

<!-- 
The Query Loop block is one of the most unique and useful blocks to create custom patterns for. It gives you and your theme users the ability to quickly insert or replace existing Query blocks with an alternative posts layout.
 -->

「クエリー・ループ」ブロックは、カスタム・パターンを制作する際に最もユニークで役立つブロックの一つです。これを使用することで、あなたとあなたのテーマのユーザーは、既存のクエリー・ブロックを、代替の投稿レイアウトに迅速に挿入または置換する機能を手にできます。

<!-- 
The technique is the same as other block type patterns. You must add the `core/query` block type to the pattern’s `Block Types` file header field.
 -->

この技術は他のブロック・タイプ・パターンと同じです。パターンの `Block Types` ファイル・ヘッダー・フィールドに、`core/query` ブロック・タイプを追加する必要があります。

<!-- 
Let’s create a basic two-column grid that shows each post’s featured image, title, excerpt and date. You can, of course, use whatever layout and design that you want.
 -->

基本的な2カラム・グリッドを作成し、各投稿のフィーチャー画像、タイトル、抜粋、日付を表示してみましょう。もちろん、お好みのレイアウトやデザインも使用できます。

<!-- 
For now, create a new `query-two-columns.php` file in your theme’s `/patterns` folder and paste this code into it:
 -->

次に、あなたのテーマの `/patterns` フォルダー内に新規 `query-two-columns.php` ファイルを作成し、以下のコードをペーストします:

```php
<?php
/**
 * Title: Query: Two Columns
 * Slug: themeslug/query-two-columns
 * Categories: posts
 * Block Types: core/query
 * Viewport Width: 1376
 */
?>
<!-- wp:query {"query":{"perPage":6,"pages":0,"offset":0,"postType":"post","order":"desc","orderBy":"date","author":"","search":"","exclude":[],"sticky":"","inherit":false},"align":"wide"} -->
<div class="wp-block-query alignwide">
		<!-- wp:post-template {"style":{"spacing":{"blockGap":"var:preset|spacing|40"}},"layout":{"type":"grid","columnCount":2}} -->
		<!-- wp:post-featured-image {"isLink":true,"aspectRatio":"4/3","align":"wide"} /-->
		<!-- wp:post-title {"isLink":true,"fontSize":"large"} /-->
		<!-- wp:post-excerpt {"showMoreOnNewLine":false,"excerptLength":26} /-->
		<!-- wp:post-date /-->
	<!-- /wp:post-template -->
</div>
<!-- /wp:query -->
```

<!-- 
There are two ways to take advantage of Query Loop patterns, like the one you just created. The first is to insert a new Query Loop block into a page or template:
 -->

先ほど作成したものと同様、「クエリー・ループ」パターンの活用には、2つの方法があります。まず1つ目は、ページやテンプレートに新規「クエリー・ループ」ブロックを挿入する方法です:

<!-- 
[![Query Loop block inserted into the WordPress block editor with the initial prompt to choose a pattern.](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-start.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-start.webp?ssl=1)
 -->

[![パターンを選択する為の最初の催促が表示されている、WordPress ブロック・エディターに挿入された「クエリー・ループ」ブロック。](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-start.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-start.webp?ssl=1)

<!-- 
You should see a couple of buttons for adding a Query Loop from that point. Click the **Choose** button.
 -->

それから、「クエリー・ループ」を追加するためのボタンが、いくつか表示されるでしょう。**選択** ボタンをクリックします。

<!-- 
This will bring up the **Choose a pattern** modal. In this modal, your pattern will appear and can be selected:
 -->

**パターンを選択** モーダルが表示されます。このモーダルでは、あなたのパターンが表示され、選択できます:

<!-- 
[![Modal overlaying the post editor that shows three options of different patterns for showing a list or grid of posts.](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-modal.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-modal.webp?ssl=1)
 -->

[![投稿のリストまたはグリッドを表示するための3パターンのオプションを表示する、投稿エディターにオーバーレイするモーダル。](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-modal.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-modal.webp?ssl=1)

<!-- 
Once selected, your pattern will be inserted into the canvas of the page or template that you are editing:
 -->

選択すると、編集中のページやテンプレートのキャンバスに、あなたのパターンが挿入されます:

<!-- 
[![WordPress post editor with a two-column grid of posts shown in the content area.](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-inserted.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-inserted.webp?ssl=1)
 -->

[![投稿の2カラム・グリッドがコンテンツ・エリアに表示される、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-inserted.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/query-loop-inserted.webp?ssl=1)

<!-- 
The second method of using Query Loop patterns is much the same. You can replace an existing pattern (even the one you just inserted) by clicking the **Replace** button in the toolbar. It will bring up the same **Choose a pattern** modal, and the process of choosing a pattern is the same.
 -->

「クエリー・ループ」パターンを使う2つ目の方法は、ほとんど同じです。ツールバーの **置換** ボタンをクリックすると、(挿入したばかりのパターンでも) 既存パターンを置換できます。同様に **パターンを選択** モーダルが表示され、パターンを選択するプロセスも同様です。

<!-- 
## Template Part patterns
 -->

## 「テンプレート・パーツ」パターン

<!-- 
Because [template parts](https://developer.wordpress.org/themes/templates/template-parts/) are technically blocks themselves, you can also use them as a pattern’s block types. There is one limitation: only parts that use the Header and Footer [template part areas](https://developer.wordpress.org/themes/templates/template-parts/#template-part-areas) are supported. But these are the most common types anyway.
 -->

[テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) は技術的にはブロックそのものですので、パターンのブロック・タイプとして使うこともできます。ひとつだけ制限があり、「ヘッダー」および「フッター」[テンプレート・パーツ・エリア](https://developer.wordpress.org/themes/templates/template-parts/#template-part-areas) を使用するパーツだけが対応します。いずれにしても、これらは最も一般的なタイプです。

<!-- 
When targeting a specific template part, its block type name will have a third component: the template part area. So if you want to target the Header part, you will pass a block type of `core/template-part/header`. And for the Footer part, use `core/template-part/footer`.
 -->

特定のテンプレート・パーツをターゲットにする場合には、そのブロック・タイプ名称は3番目の要素、テンプレート・パーツ・エリア、を持つことになります。つまり、「ヘッダー」パーツをターゲットにしたい場合は、`core/template-part/header` のブロック・タイプを渡すことになります。そして「フッター」パーツの場合は、`core/template-part/footer` を使います。

<!-- 
Let’s create a basic Header template part with a centered logo, title, and nav menu. You will use this to replace the existing header on your site.
 -->

ロゴ、タイトル、ナビメニューを中央に配置した、基本的な「ヘッダー」テンプレート・パーツを制作してみましょう。これは、あなたのサイトの既存ヘッダーを置換するために使用します。

<!-- 
Create a new file named `header-centered.php` in your theme’s `/patterns` folder. Then copy and paste this code into it:
 -->

あなたのテーマの `/patterns` フォルダーに `header-centered.php` という名前の新規ファイルを作成しましょう。それに以下のコードをコピー & ペーストします:

```php
<?php
/**
 * Title: Header: Centered
 * Slug: themeslug/header-centered
 * Categories: header
 * Block Types: core/template-part/header
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","layout":{"type":"flex","orientation":"vertical","justifyContent":"center"}} -->
<div class="wp-block-group alignwide">
	<!-- wp:site-logo {"width":60} /-->
	<!-- wp:site-title {"level":0} /-->
	<!-- wp:navigation {"layout":{"type":"flex","justifyContent":"right","orientation":"horizontal"},"style":{"spacing":{"margin":{"top":"0"},"blockGap":"var:preset|spacing|20"},"layout":{"selfStretch":"fit","flexSize":null}}} /-->
</div>
<!-- /wp:group -->
```

<!-- 
Once you save this file, go to **Appearance > Editor** in your WordPress admin and select the on the Header block.
 -->

このファイルを保存したら、WordPress 管理画面の **外観 > エディター** から「ヘッダー」ブロックを選択します。

<!-- 
Now click the **Options** button (**⋮** icon) in the toolbar. You should see a **Replace** option in the dropdown:
 -->

では、ツールバーの **オプション** ボタン (**⋮** アイコン) をクリックします。ドロップダウンに **置換** オプションが表示されるはずです:

<!-- 
[![WordPress Site Editor with the Header Template Part selected in the content area. The Options dropdown shows the "Replace" item highlighted.](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-part-replace-dropdown.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-part-replace-dropdown.webp?ssl=1)
 -->

[![WordPress サイト・エディターのコンテンツ・エリアで、「ヘッダー・テンプレート・パーツ」を選択した状態。「オプション」ドロップダウンでは、「置換」項目が強調表示されている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-part-replace-dropdown.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-part-replace-dropdown.webp?ssl=1)

<!-- 
Once you click the **Replace** dropdown menu item, a new modal titled **Choose a header** will appear, and you should see your **Header: Centered** pattern in the available patterns grid:
 -->

**置換** ドロップダウン・メニュー項目をクリックすると、**ヘッダーを選択** と題された新規モーダルが表示され、使用可能なパターン・グリッドに、あなたの **ヘッダー: 中央そろえ** パターンが表示されるはずです:

<!-- 
[![A modal overlaying the Site Editor screen that reads "Choose a header." Below, it shows a grid of various site header designs to choose from.](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-pattern-replace.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-pattern-replace.webp?ssl=1)
 -->

[![サイト・エディター画面にオーバーレイ表示される、「ヘッダーを選択」と書かれたモーダル。その下には、さまざまなサイトヘッダー・デザインから選べる、グリッドが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-pattern-replace.webp?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/header-pattern-replace.webp?ssl=1)

<!-- 
By selecting this pattern or another, you can replace the entire Header template part. This process works the same for Footer template parts.
 -->

このパターンまたは別のパターンを選択することで、「ヘッダー」テンプレート・パーツ全体を置換できます。このプロセスは「フッター」テンプレート・パーツでも、同じように機能します。

<!-- 
Parts for custom [template part areas](https://developer.wordpress.org/themes/templates/template-parts/#template-part-areas) cannot yet take advantage of this feature. There is an [open ticket](https://github.com/WordPress/gutenberg/issues/44689) that has not been patched to handle areas other than Header and Footer.
 -->

カスタム [テンプレート・パーツ・エリア](https://developer.wordpress.org/themes/templates/template-parts/#template-part-areas) 用のパーツは、まだこの機能の恩恵を受けることができません。「ヘッダー」と「フッター」以外の領域を扱うためのパッチが適用されていない旨の [オープン・チケット](https://github.com/WordPress/gutenberg/issues/44689) があります。