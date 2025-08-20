<!-- 
# Block Patterns (Archived)
 -->

# ブロック・パターン (アーカイブ済み)

<!-- 
This documentation article has now been archived and replaced with the newer [Patterns chapter](https://developer.wordpress.org/themes/patterns/) of the Theme Handbook. Please refer to that page for the most up-to-date information on patterns.
 -->

このドキュメント記事は現在アーカイブされ、テーマハンドブックの新しい [パターンの章](https://developer.wordpress.org/themes/patterns/) に置き換えられました。パターンに関する最新の情報は、そのページをご参照ください。

<!-- 
Block patterns are one of the most powerful features at a theme author’s disposal. Introduced in WordPress 5.4, patterns made it easier for users to insert more complex layouts from the block editor while opening a world of possibilities to designers.
 -->

ブロック・パターンは、テーマ作成者が利用できる最も強力な機能の一つです。WordPress 5.4で導入されたパターンは、ユーザーがブロック・エディターからより複雑なレイアウトを挿入しやすくする一方で、デザイナーに無限の可能性を開きました。

<!-- 
## What are block patterns? 
 -->

## ブロック・パターンって ?  

<!-- 
Essentially, a block pattern is nothing more than one or more blocks that have been pre-configured and presented to the end-user. Think of them as reusable groups of blocks.
 -->

本質的に、ブロック・パターンとは、事前に設定され、エンドユーザーに提示される1つまたは複数のブロックに過ぎません。それらを再利用可能なブロックのグループと考えることができます。

<!-- 
They are ideal as starting points for users to insert into their post and page content, but they are also useful when used inside of templates.
 -->

これらは、ユーザーが投稿やページのコンテンツに挿入する際の最適な出発点として機能しますが、テンプレート内での使用にも役立ちます。

<!-- 
Users can insert them directly into a template from the Site Editor or into their content from the Post Editor:
 -->

ユーザーは、「サイト・エディター」からテンプレートに直接挿入したり、「投稿エディター」からコンテンツに直接挿入したりできます:

<!-- 
[![WordPress post editor with the Inserter open and the Patterns tab selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert.jpg?ssl=1)
 -->

[![「インサーター」を開き、「パターン」タブを選択した、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert.jpg?ssl=1)

<!-- 
In comparison to [template parts](https://developer.wordpress.org/themes/templates/template-parts/), which is a similar feature for reusable groups of blocks, patterns also give you access to PHP. This means that you can internationalize text within them, dynamically add URLs to include images, and more.
 -->

ブロックの再利用可能なグループのための類似の機能である、[テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) と比べて、パターンも PHP へのアクセスを可能にします。これは、それらの中でテキストを国際化したり、画像を含む URL を動的に追加したり、さらに多くの機能を利用できることを意味します。

<!-- 
Note that users can also create and manage custom patterns from the **Appearance > Editor > Patterns** screen in the admin. You can also use this screen to manage your own patterns in your development install:
 -->

ユーザーは、管理画面の **外観 > エディター > パターン** 画面から、カスタム・パターンを作成および管理もできる点に注意してください。この画面を使用して、開発環境でのインストールにおいて、独自のパターンも管理できます:

<!-- 
[![WordPress patterns library in the admin showing the All Patterns screen. On the right, a three-column grid of patterns are shown in preview boxes.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-all.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-all.jpg?ssl=1)
 -->

[![「すべてのパターン」画面を表示している、管理画面内の WordPress パターン・ライブラリ。右側には、プレビュー・ボックス内にパターンの3列グリッドが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-all.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-all.jpg?ssl=1)

<!-- 
## Working with block patterns
 -->

## ブロック・パターンの扱い方

<!-- 
In this section, you will learn how to create custom block patterns, register them in your theme, and unregister them. You will also learn some useful tips, tricks, and other methods for working with patterns.
 -->

このセクションでは、カスタム・ブロック・パターンを制作し、あなたのテーマに登録したり、登録解除する方法について学びます。パターンの扱い方に関する役立つヒントやテクニック、その他の方法も学ぶことができます。

<!-- 
### Creating block patterns
 -->

### ブロック・パターンの制作

<!-- 
The easiest way to learn to create block patterns is to start by putting a few blocks together in the Post Editor. This can be anything you like, but for the purposes of this article, the code shared below will be of a core Cover block with some blocks nested within it, following this structure:
 -->

ブロック・パターンを制作する最も簡単な方法は、「投稿エディター」でいくつかのブロックを組み合わせて始めることです。これは何でもかまいませんが、本稿の目的上、以下のコードは、内部にいくつかのブロックがネストされた、コア「カバー」ブロックの例で、その構造は次の通りです:

*   Group
    *   Heading
    *   Paragraph
    *   Buttons
        *   Button

<!-- 
Try recreating this yourself, especially if you are just getting used to working with the block editor. You can also customize this however you like, but it’s recommended to keep this relatively simple for your first time creating a pattern.
 -->

特にブロック・エディターに不慣れな人は、このパターンを自分で再現してみてください。このパターンは自由にカスタマイズできますが、初めてパターンを制作する際は、比較的シンプルに保つことをおすすめします。

<!-- 
Once you’re finished, click the **⋮** (Options) icon in the toolbar and click **Copy**:
 -->

完了したら、ツールバーの **⋮** (オプション) アイコンをクリックし、**「コピー」** をクリックしてください:

<!-- 
[![WordPress post editor with a Cover block in the content canvas. A dropdown is open from the toolbar with the Copy button highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-create-copy.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-create-copy.jpg?ssl=1)
 -->

[![コンテンツ・キャンバスに「カバー」ブロックを配した WordPress 投稿エディター。ツールバーからドロップダウンが開き、「コピー」ボタンが強調表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-create-copy.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-create-copy.jpg?ssl=1)

<!-- 
This will give you the code you need to work with, which should be similar to this:
 -->

これにより、扱うために必要なコードが得られ、以下のような形式になるはずです:

```markup
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me.  I'll share my likes, hobbies, and more.  Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
For the remainder of this article, you will work with this same pattern, learning how to register it, unregister it, and customize it further.
 -->

本稿の残りの部分では、この同じパターンを扱って、その登録の方法、登録解除の方法、さらにカスタマイズの方法について学びます。

<!-- 
It’s good practice to wrap most patterns in a Group, Cover, or other container block (i.e., a block that allows nested blocks). This makes it easier for your theme users to move the entire pattern around in the editor. You can also add a CSS class to this outer block for any custom styling that applies to the entire pattern.
 -->

多くのパターンを「グループ」、「カバー」、またはその他のコンテナ・ブロック (つまり、ネストされたブロックを許可するブロック) で囲むことは良い習慣です。これにより、あなたのテーマのユーザーが、エディター内でパターン全体を移動させることがより簡単になります。この外側のブロックに CSS クラスを追加することで、パターン全体に適用される、任意のカスタムスタイルも適用できます。

<!-- 
### Registering block patterns
 -->

### ブロック・パターンの登録

<!-- 
There are two methods for registering block patterns in WordPress:
 -->

WordPress でブロック・パターンの登録には2つの方法があります:

<!-- 
*   By placing files with block markup in them into the `/patterns` folder in your theme.
*   By manually calling the `register_block_pattern()` function.
 -->

*   あなたのテーマ内の `/patterns` フォルダーに、ブロック・マークアップを含むファイルを配置する。
*   `register_block_pattern()` 関数を手動で呼び出す。

<!-- 
The most straightforward route is the first. You’ll learn how to do both in the next sections, but this handbook will recommend using the `/patterns` folder except for in some edge cases.
 -->

最も直感的な方法は、最初の方法です。次のセクションで両方の方法を学びますが、本ハンドブックでは、一部の特殊なケースを除き、`/patterns` フォルダーの使用を推奨します。

<!-- 
#### Using the /patterns directory to register patterns
 -->

#### `/patterns` ディレクトリを使用した、パターンの登録

<!-- 
WordPress will recognize any pattern file placed in your theme’s `/patterns` folder, and it will automatically register it for you, provided that it has a valid pattern file header.
 -->

WordPress は、あなたのテーマの `/patterns` フォルダーに置かれたパターンファイルを認識し、そのパターンファイルが有効なパターンファイル・ヘッダーを持っている場合、自動的に登録します。

<!-- 
A [file header](https://codex.wordpress.org/File_Header) is PHP-commented code with a list of key + value pairs at the top of a file. WordPress parses this information to gather metadata. In this case, the metadata is used to register a block pattern.
 -->

[ファイル・ヘッダー](https://codex.wordpress.org/File_Header) とは、ファイルの先頭にあるキー・値ペアのリストを含む、PHP コメント付きのコードのことです。WordPress はこの情報を解析して、メタデータを収集します。この場合、メタデータはブロック・パターンの登録に使用されます。

<!-- 
For pattern file headers, these are the keys that you can set:
 -->

パターンファイル・ヘッダーでは、以下のキーを設定できます:

<!-- 
*   **`Title`:** A human-readable title that can be translated.
*   **`Slug`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`Categories`:** A comma-separated list of categories in which the pattern belongs.
*   **`Description`:** The long description of the registered pattern. Only shown to screen readers.
*   **`Viewport Width`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
*   **`Inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
*   **`Keywords`:** A comma-separated list of keywords related to the pattern for search.
*   **`Block Types`:** A comma-separated list of block types to associate the pattern with.
*   **`Post Types`:** A comma-separated list of post types in which to limit the pattern. Defaults to all post types.
*   **`Template Types`:** A comma-separated list of template types the pattern fits with.
 -->

*   **`Title`:** 翻訳可能な、人間可読タイトルです。
*   **`Slug`:** あなたのパターンに固有の、`namespace/pattern-name` 形式の、名前空間付きスラッグです。
*   **`Categories`:** パターンが属するカテゴリーの、カンマ区切りリストです。
*   **`Description`:** 登録されたパターンの、長文説明です。スクリーンリーダーにのみ表示されます。
*   **`Viewport Width`:** パターンをプレビューする際の `<iframe>` ビューポートの幅 (ピクセル単位) です。
*   **`Inserter`:** インサーターにパターンを表示するかどうかです。デフォルトは `true` です。
*   **`Keywords`:** 検索の対象となるパターンに関連するキーワードの、カンマ区切りリストです。
*   **`Block Types`:** パターンと協働するブロックタイプの、カンマ区切りリストです。
*   **`Post Types`:** パターンを制限する投稿タイプの、カンマ区切りリストです。デフォルトはすべての投稿タイプです。
*   **`Template Types`:** パターンに適合するテンプレート・タイプの、カンマ区切りリストです。

<!-- 
For most patterns, you should at least add the `Title`, `Slug`, and `Categories` fields. Pattern files should look like this:
 -->

ほとんどのパターンでは、少なくとも `Title`、`Slug`、`Categories` フィールドを追加する必要があります。パターンファイルは、次のようになります:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- Pattern code goes here. -->
```

<!-- 
Now let’s add the code that you copied from the previous section into the `/patterns/hero.php` file in your theme:
 -->

では、前のセクションからコピーしたコードを、あなたのテーマ内の `/patterns/hero.php` ファイルに追加しましょう:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
Now if you add or edit a new post in WordPress, you should see your pattern listed in the inserter. Click the **Patterns** tab and select **Featured**:
 -->

さて、WordPress で新規投稿を追加または編集すると、インサーターにパターンが一覧表示されるはずです。**パターン** タブをクリックし、**注目** を選択してください:

<!-- 
[![WordPress post editor with the Patterns > Featured category selected in the Inserter. A single pattern is listed.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert-custom.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert-custom.jpg?ssl=1)
 -->

[![「インサーター」で、「パターン > 注目」カテゴリーが選択された WordPress 投稿エディター。1つのパターンがリストされている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert-custom.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-insert-custom.jpg?ssl=1)

<!-- 
You should also be able to see your pattern listed under **Appearance > Editor > Patterns** in the WordPress admin.
 -->

また、WordPress 管理画面の **外観 > エディター > パターン** 以下に、あなたのパターンがリストアップされているはずです。

<!-- 
#### Using PHP to register patterns
 -->

#### PHP を使用した、パターンの登録

<!-- 
Instead of using the `/patterns` folder to auto-register your patterns, you may choose to manually register them via PHP. You can mix and match both registration methods, but an individual pattern must be registered with only one method.
 -->

`/patterns` フォルダーを使用してパターンを自動登録する代わりに、PHP 経由での手動登録も選択できます。両方の登録方法を組み合わせて使用できるが、個々のパターンは、1つの方法のみで登録する必要があります。

<!-- 
To register block patterns with PHP, you must use the [`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) function. Here is what its signature looks like:
 -->

PHP でブロック・パターンを登録するには、[`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) 関数を使用する必要があります。そのシグネチャは次のようなものです:

```php
register_block_pattern( 
	string $pattern_name, 
	array $pattern_properties 
): bool
```

<!-- 
The function accepts two parameters and returns `true` or `false`, depending on whether the pattern was successfully registered:
 -->

この関数は2つのパラメータを受け取り、パターンが正常に登録されたかどうかによって、`true` または `false` を返します:

<!-- 
*   **`$pattern_name`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`$pattern_properties`:**
    *   **`content`:** The block markup for the pattern.
    *   **`title`:** A human-readable title that can be translated.
    *   **`slug`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
    *   **`categories`:** An array of categories in which the pattern belongs.
    *   **`description`:** The long description of the registered pattern. Only shown to screen readers.
    *   **`viewportWidth`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
    *   **`inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
    *   **`keywords`:** An array of keywords related to the pattern for search.
    *   **`blockTypes`:** An array of block types to associate the pattern with.
    *   **`postTypes`:** An array of post types in which to limit the pattern. Defaults to all post types.
    *   **`source`:** The source for the registered pattern. This should be set to `theme` since the pattern is coming from a theme.
    *   **`templateTypes`:** An array of template types the pattern fits with.
 -->

*   **`$pattern_name`:** あなたのパターンに固有の、`namespace/pattern-name` 形式の、名前空間付きスラッグです。
*   **`$pattern_properties`:**
    *   **`content`:** パターン用の、ブロック・マークアップです。
    *   **`title`:** 翻訳可能な、人間可読タイトルです。
    *   **`slug`:** あなたのパターンに固有の、`namespace/pattern-name` 形式の、名前空間付きスラッグです。
    *   **`categories`:** パターンが属するカテゴリーの、配列です。
    *   **`description`:** 登録されたパターンの、長文説明です。スクリーンリーダーにのみ表示されます。
    *   **`viewportWidth`:** パターンをプレビューする際の `<iframe>` ビューポートの幅 (ピクセル単位) です。
    *   **`inserter`:** インサーターにパターンを表示するかどうかです。デフォルトは `true` です。
    *   **`keywords`:** 検索の対象となるパターンに関連するキーワードの、配列です。
    *   **`blockTypes`:** パターンと協働するブロックタイプの、配列です。
    *   **`postTypes`:** パターンを制限する投稿タイプの、配列です。デフォルトはすべての投稿タイプです。
    *   **`source`:** 登録されたパターン用の出典です。これは、パターンがテーマから由来してきているため、`theme` に設定する必要があります。
    *   **`templateTypes`:** パターンに適合するテンプレート・タイプの、配列です。

<!-- 
When registering patterns via PHP, you should do so on the `init` hook. Now try registering your custom pattern by adding this code in `functions.php` (be sure to add your custom markup to the `content` property):
 -->

PHP 経由でパターンを登録する際は、`init` フックで実施する必要があります。では、`functions.php` にこのコードを追加して、あなたのカスタム・パターンを登録してみてください (`content` プロパティにあなたのカスタム・マークアップを、必ず追加してください):

```php
add_action( 'init', 'themeslug_register_patterns' );

function themeslug_register_patterns() {
	register_block_pattern( 'themeslug/hero', array(
		'title'      => __( 'Hero', 'themeslug' ),
		'categories' => array( 'featured' ),
		'source'     => 'theme',
		'content'    => '<!-- Block pattern goes here. -->'
	) );
}
```

<!-- 
### Including patterns in templates
 -->

### テンプレートに、パターンの挿入

<!-- 
When building themes, patterns are not merely reusable sections of blocks that users can add to their content. That is a nice feature, but the true power of patterns is using them directly in your theme’s front-end output.
 -->

テーマを構築する際、パターンは単にユーザーがコンテンツに追加できる、再利用可能なブロックのセクションにとどまりません。それは便利な機能ですが、パターンの真の力は、あなたのテーマのフロントエンド出力に、直接使用することにあります。

<!-- 
You can include patterns in your [templates](https://developer.wordpress.org/themes/templates/templates/) or [template parts](https://developer.wordpress.org/themes/templates/template-parts/) by adding the Pattern block markup and passing along the pattern slug.
 -->

「パターン」ブロック・マークアップを追加し、パターン・スラッグを伝達することで、あなたの [テンプレート](https://developer.wordpress.org/themes/templates/templates/) や [テンプレート・パーツ](https://developer.wordpress.org/themes/templates/template-parts/) にパターンを含めることができます。

<!-- 
Here is what the Pattern block markup would look like when calling your existing “hero” pattern:
 -->

既存の「hero」パターンをコールする際の「パターン」ブロック・マークアップは、次のようになります:

```markup
<!-- wp:pattern {"slug":"themeslug/hero"} /-->
```

<!-- 
That should be relatively straightforward. All you need to know is the `slug` value from when you registered the pattern.
 -->

それは比較的、直感的です。パターンを登録する際は、単に `slug` 値を把握していれば十分です。

<!-- 
Now try adding it to one of your theme’s templates, such as `/templates/home.html` or `/templates/index.html` below the header. Your template with the pattern code should look similar to this:
 -->

では、テーマのテンプレートの一つ、たとえば、ヘッダー以下にある `/templates/home.html` または `/templates/index.html` などに、それを追加してみてください。パターン・コードを含むあなたのテンプレートは、次のようになります:

```markup
<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:pattern {"slug":"themeslug/hero"} /-->

<!-- Some other blocks. /-->

<!-- wp:template-part {"slug":"footer"} /-->
```

<!-- 
Now test the addition of the pattern in the Site Editor by going to **Appearance > Editor > Templates** and choosing the template you added it to:
 -->

では、**外観 > エディター > テンプレート** に移動し、追加したテンプレートを選択することで、「サイト・エディター」でパターンの追加をテストします:

<!-- 
[![WordPress Site Editor showing the Blog posts index template. The content shows a Header template part and a block pattern with the Cover block beneath it.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-template-include.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-template-include.jpg?ssl=1)
 -->

[![「ブログ」投稿インデックス・テンプレートを表示する WordPress「サイト・エディター」。「ヘッダー」テンプレート・パーツと、その下に「カバー」ブロックを含むブロック・パターンが表示されているコンテンツ。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-template-include.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-template-include.jpg?ssl=1)

<!-- 
### Unregistering block patterns
 -->

### ブロック・パターンの登録解除

<!-- 
There are times when you need to unregister block patterns so that they do not appear in the inserter for users. For example, you may want to remove some of the core WordPress patterns, those added by a parent theme (if you’re building a child theme), or those added by third-party plugins.
 -->

ブロック・パターンを登録解除して、ユーザーのインサーターに表示されないようにする必要がある場合があります。たとえば、コア WordPress パターン、または、(子テーマを構築している場合は) 親テーマによって追加されたパターン、あるいは、サードパーティーのプラグインによって追加されたパターンを削除したい場合があります。

<!-- 
When you need to unregister a single block pattern, you’ll use the [`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) function:
 -->

単一のブロック・パターンを登録解除する必要がある場合、[`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) 関数を使用します:

```php
unregister_block_pattern( string $pattern_name ): bool
```

<!-- 
Like when registering patterns, you’ll also want to unregister on the `init` hook. Because patterns are generally (but not always) registered with the default priority `10` on `init`, you’ll want to use a higher priority so that your code runs later.
 -->

パターンを登録するときと同様に、`init` フックで登録解除する必要があります。パターンは一般的にデフォルトの優先度 `10` で (ただし常にではない)、`init` に登録されるため、コードを後で実行させるためには、より高い優先度を使用する必要があります。

<!-- 
Try unregistering your custom pattern from earlier by adding this code to your `functions.php` file:
 -->

このコードを `functions.php` ファイルに追加することで、以前に登録したあなたのカスタム・パターンを登録解除してみてください:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	unregister_block_pattern( 'themeslug/hero' );
}
```

<!-- 
### Removing core patterns
 -->

### コアパターンの削除

<!-- 
While you can use `unregister_block_pattern()` to unregister individual core WordPress patterns, you can also choose to get rid of all of them by removing support for the `core-block-patterns` feature.
 -->

`unregister_block_pattern()` を使用すると、個々のコア WordPress パターンを登録解除できるが、`core-block-patterns` 機能のサポートを削除することでも、それらすべてを削除できます。

<!-- 
To remove all core WordPress patterns, add this code to your theme’s `functions.php` file:
 -->

コア WordPress パターンをすべて削除するには、このコードをあなたのテーマの `functions.php` ファイルに追加してください:

```php
add_action( 'after_setup_theme', 'themeslug_remove_core_patterns' );

function themeslug_remove_core_patterns() {
	remove_theme_support( 'core-block-patterns' );
}
```

<!-- 
### Disabling remote patterns
 -->

### リモート・パターンの無効化

<!-- 
WordPress also automatically loads some patterns remotely from the official [Pattern Directory](https://wordpress.org/patterns/) on WordPress.org. There are some situations where you might not want to load these patterns, such as when they don’t match your theme design. You may also want to opt out of calling a remote API on a site that you’re building for a client. Whatever the case, you can disable this by filtering the [`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) hook.
 -->

WordPress は、WordPress.org の公式 [パターン・ディレクトリ](https://wordpress.org/patterns/) から一部のパターンをリモートで自動的にロードします。これらのパターンをロードしたくない状況もあり、たとえば、あなたのテーマ設計と合致しない場合などが挙げられます。クライアント向けに構築しているサイトにおいて、リモート API へのコールを無効にしたい場合もあるでしょう。いずれにせよ、[`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) フックをフィルタリングすることで、これを無効化できます。

<!-- 
To disable remote patterns, add this code to your `functions.php` file:
 -->

リモート・パターンを無効化するには、このコードをあなたの `functions.php` ファイルに追加してください:

```php
add_filter( 'should_load_remote_block_patterns', '__return_false' );
```

<!-- 
### Tips and tricks
 -->

### ヒントとコツ

<!-- 
Below, you’ll find various tips, tricks, and other useful features that make block patterns a powerful and flexible part of WordPress theme development.
 -->

以下では、ブロック・パターンを WordPress テーマ開発において強力かつ柔軟なパーツとする、さまざまなヒント、テクニック、その他の便利な機能を紹介します。

<!-- 
#### Internationalizing text in patterns
 -->

#### パターン内のテキストの国際化

<!-- 
One of the primary use cases for block patterns is [internationalizing text](https://developer.wordpress.org/themes/functionality/internationalization/) (making it ready for translation). For example, if you have text in a template or template part, the only way to internationalize that text is to move it into a pattern, where you have full access to PHP.
 -->

ブロック・パターンの主なユースケースの一つは [テキストの国際化](https://developer.wordpress.org/themes/functionality/internationalization/) (翻訳に対応できるようにすること) です。たとえば、テンプレートまたはテンプレート・パーツにあるテキストを国際化するには、PHP に完全なアクセス権限があるパターン内に、そのテキストを移動させる必要があります。

<!-- 
Because pattern files are just PHP, you can use any of the internationalization functions within WordPress. In the below example, you’ll use [`esc_html_e()`](https://developer.wordpress.org/reference/functions/esc_html_e/) to both escape the text for security and make it ready for translators.
 -->

パターンファイルは単なる PHP であるため、WordPress 内の国際化機能はどれでも使用できます。以下の例では、[`esc_html_e()`](https://developer.wordpress.org/reference/functions/esc_html_e/) を使用して、テキストをセキュリティのためにエスケープし、翻訳者向けに準備します。

<!-- 
Try taking your “hero” pattern example and wrapping the custom text inside the Heading, Paragraph, and Button blocks with the `esc_html_e()` function. Your pattern file should look like this:
 -->

あなたの「hero」パターン例を試して、`esc_html_e()` 関数で、カスタム・テキストを「見出し」、「段落」、「ボタン」ブロック内にラップしてみてください。あなたのパターンファイルは、次のようになります:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ) ?></h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center"><?php esc_html_e( "This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.", 'themeslug' ) ?></p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'See My Popular Posts →', 'themeslug' ) ?></a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
#### Using images and other assets
 -->

#### 画像やその他のアセットの使用

<!-- 
Adding dynamic URLs for images and other assets is another important feature of patterns. Because you have PHP access, you can use functions like `get_theme_file_uri()` to output an image URL that’s bundled with your theme, for example.
 -->

画像やその他のアセット用の動的 URL の追加は、パターンのもう一つの重要な機能です。PHP へのアクセス権限があるため、たとえば、あなたのテーマにバンドルされている画像の URL を出力するために、`get_theme_file_uri()` のような関数を使用できます。

<!-- 
Try adding an image background to your “hero” pattern’s Cover block. If you need an image, try grabbing one from the WordPress [Photo Directory](https://wordpress.org/photos/) (the example below uses this [Nepal night scene photo](https://wordpress.org/photos/photo/41664fab9b/)). 
 -->

あなたの「ヒーロー」パターンの「カバー」ブロックに画像の背景を追加してみましょう。画像が必要な場合は、WordPress [写真ディレクトリ](https://wordpress.org/photos/) から入手しましょう (以下の例では、この [ネパールの夜景の写真](https://wordpress.org/photos/photo/41664fab9b/) を使用)。

<!-- 
Download an image and save it to your theme’s `/assets/images` folder (or a folder of your choice) and name it `hero-background.jpg`.
 -->

画像をダウンロードし、あなたのテーマの `/assets/images` フォルダー (または任意のフォルダー) に保存し、`hero-background.jpg` と名付けます。

<!-- 
Then open your pattern in the editor and upload the image as the background for the Cover block, which should look like this:
 -->

では、エディターであなたのパターンを開き、「カバー」ブロックの背景として画像をアップロードすると、次のように表示されます:

<!-- 
[![WordPress post editor showing a Cover block with a background image of a cityscape.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-cover-with-background.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-cover-with-background.jpg?ssl=1)
 -->

[![街並みの背景画像を使用した「カバー」ブロックを表示する、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-cover-with-background.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-cover-with-background.jpg?ssl=1)

<!-- 
As you did earlier, copy the blocks that make up the pattern. You’ll notice that you have two instances of the image URL in your pattern code. It will be a hardcoded URL similar to this:
 -->

先ほどと同様に、パターンを構成するブロックをコピーします。あなたのパターン・コードに、画像の URL が2つ含まれていることに気付くでしょう。次のようなハードコードされた URL になります:

```markup
http://localhost/wp/wp-content/uploads/2023/10/hero-background.jpg
```

<!-- 
You need to change both of those instances so that they point to the image that is located in your theme’s `/assets/images` folder. For this, you need do two things:
 -->

これらの2つのインスタンスを両方とも変更し、あなたのテーマの `/assets/images` フォルダー内に格納されている画像を指すようにする必要があります。これには、次の2つのことを実施する必要が
あります:

<!-- 
*   Get the correct URL using a function like [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/).
*   Escape the URL so that it’s safe for output with [`esc_url()`](https://developer.wordpress.org/reference/functions/esc_url/).
 -->

*   [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) のような関数を使用して、正しい URL を取得します。
*   URL をエスケープし、[`esc_url()`](https://developer.wordpress.org/reference/functions/esc_url/) で、安全に出力できるようにします。

<!-- 
Change the hard coded image URLs to this:
 -->

ハードコードされた画像の URL を、次のように変更します:

```php
<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ) ?>
```

<!-- 
Your final pattern code should look like this (note that this example includes internationalized text as explained in the previous section):
 -->

あなたの最終的なパターン・コードは次のようになります (この例には、前のセクションで説明した国際化テキストが含まれていることに注意すること):

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ) ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span><img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ) ?>" data-object-fit="cover"/><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ) ?></h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center"><?php esc_html_e( "This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.", 'themeslug' ) ?></p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'See My Popular Posts →', 'themeslug' ) ?></a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
#### Conditionally loading third-party blocks
 -->

#### サードパーティーのブロックの条件付きロード

<!-- 
There are times when you might want to only use a block if it is registered on the user’s install. This is particularly true for third-party blocks that may be contained in a plugin.
 -->

ユーザーがインストールしたプラグインにブロックが登録されている場合、ブロックのみを使用したい場合があるかもしれません。これは特に、プラグインに含まれる可能性のある、サードパーティー・ブロックに当てはまります。

<!-- 
It’s important to note that WordPress will prompt a user to install the block if you add its block markup and it’s not installed. It won’t result in a broken website, so it’s OK to avoid using the method described in this section.
 -->

そのブロック・マークアップを追加しても、それがインストールされていない場合、WordPress はユーザーにブロックのインストールを促すことに注意してください。このセクションで説明されている方法を使用しなくても、Web サイトが破損する心配はないので、問題ありません。

<!-- 
But if you would prefer to hide an unregistered block (or use an alternative), you can conditionally check if a block is registered via the [`WP_Block_Type_Registry::is_registered()`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/is_registered/) method.
 -->

ただし、未登録ブロックを非表示にしたい (または代替手段を使用したい) 場合、[`WP_Block_Type_Registry::is_registered()`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/is_registered/) メソッド経由でブロックが登録されているか否かを条件付きで確認できます。

<!-- 
This example code shows how to check for the `core/paragraph` block. If it’s registered, it will output the block markup:
 -->

このサンプルコードは、`core/paragraph` ブロックの有無を確認する方法を示しています。登録されている場合、ブロック・マークアップが出力されます:

```php
<?php if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) : ?>
	<!-- Add your block markup here. -->
<?php endif ?>
```

<!-- 
Try applying this method to your registered “hero” block from earlier by wrapping the Paragraph block in this conditional check. Here’s what your pattern code should look like:
 -->

この条件分岐で「段落」ブロックをラップすることで、以前に登録した「ヒーロー」ブロックに、この方法を適用してみましょう。あなたのパターン・コードは次のようになります:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ) ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span><img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ) ?>" data-object-fit="cover"/><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ) ?></h2>
<!-- /wp:heading -->

<?php if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) : ?>
	<!-- wp:paragraph {"align":"center"} -->
	<p class="has-text-align-center"><?php esc_html_e( "This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.", 'themeslug' ) ?></p>
	<!-- /wp:paragraph -->
<?php endif ?>

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'See My Popular Posts →', 'themeslug' ) ?></a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
Of course, since the Paragraph block is registered by core WordPress and assuming it hasn’t been unregistered, your Paragraph block should appear in the editor and on the front end. The primary use case for this is to conditionally check third-party blocks.
 -->

もちろん、「段落」ブロックは、コア WordPress によって登録されており、登録解除されていない場合、あなたの「段落」ブロックは、エディターとフロントエンドの両方に表示されるはずです。この機能の主なユースケースは、サードパーティー・ブロックを条件付きでチェックすることです。

<!-- 
### Conditionally registering patterns
 -->

### パターンの条件付き登録

<!-- 
If you need to conditionally register an entire pattern instead of simply conditionally outputting specific parts of it (shown in the previous section), there are two methods to choose from, depending on how you prefer to register patterns.
 -->

その特定のパーツを (前のセクションで示したように) 条件付きで出力する代わりに、パターン全体を条件付きで登録する必要がある場合、パターンを登録する方法には、好みに応じて2つの方法から選択できます。

<!-- 
#### Conditionally registering patterns in the /patterns folder
 -->

#### `/patterns` フォルダー内のパターンの、条件付き登録

<!-- 
If you have used the auto-registration method of placing your pattern in your theme’s `/patterns` folder, there is no true way to conditionally register it. What you must do in this case is unregister the pattern.
 -->

あなたのテーマの `/patterns` フォルダーにあなたのパターンを配置する自動登録メソッドを使用した場合、条件付きでそれを登録する正しい方法は存在しません。この場合、パターンを登録解除する必要があります。

<!-- 
Suppose that you wanted to only make the hero pattern you registered earlier available if the `core/paragraph` block is registered. In a real-world scenario, you’d likely be checking for a third-party block, and the `core/paragraph` block is used only for the sake of this example.
 -->

`core/paragraph` ブロックが登録されている場合、以前に登録したヒーローパターンだけを有効にしたいと仮定します。実際のシナリオでは、おそらくサードパーティー・ブロックを確認し、`core/paragraph` ブロックは、この例のためだけに使用されています。

<!-- 
Try this code inside of your `functions.php` file to unregister your previously-registered pattern:
 -->

このコードをあなたの `functions.php` ファイル内に追加して、以前に登録したパターンを登録解除しましょう:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) {
		unregister_block_pattern( 'themeslug/hero' );
	}
}
```

<!-- 
#### Conditionally registering patterns via [register\_block\_pattern()](https://developer.wordpress.org/reference/functions/register_block_pattern/)
 -->

#### [register\_block\_pattern()](https://developer.wordpress.org/reference/functions/register_block_pattern/) を経由した、パターンの条件付き登録

<!-- 
If you manually registered your patterns via PHP, you only need to wrap your call to `register_block_pattern()` with your conditional check.
 -->

PHP 経由でパターンを手動で登録した場合、`register_block_pattern()` へのあなたのコールを、条件分岐でラップするだけです。

<!-- 
Using the same example as above, try only registering your pattern if the `core/paragraph` block is registered by adding this to `functions.php`:
 -->

上記の例と同じように、`functions.php` にこれを追加することで、`core/paragraph` ブロックが登録されている場合、あなたのパターンを登録だけしてみましょう:

```php
add_action( 'init', 'themeslug_register_patterns', 999 );

function themeslug_register_patterns() {
	if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) {
		register_block_pattern( 'themeslug/hero', array(
			'title'      => __( 'Hero', 'themeslug' ),
			'categories' => array( 'featured' ),
			'source'     => 'theme',
			'content'    => '<!-- Block pattern goes here. -->'
		) );
	}
}
```

<!-- 
## Pattern categories
 -->

## パターン・カテゴリー

<!-- 
WordPress has several block pattern categories that it registers by default:
 -->

WordPress には、デフォルトで登録されているブロック・パターン・カテゴリーが、いくつかあります:

<!-- 
*   `featured`
*   `about`
*   `audio` (added in WordPress 6.4)
*   `banner`
*   `buttons`
*   `call-to-action`
*   `columns`
*   `contact`
*   `footer`
*   `gallery`
*   `header`
*   `media`
*   `portfolio`
*   `posts`
*   `query` (use `posts` instead)
*   `services`
*   `team`
*   `testimonials`
*   `text`
*   `video` (added in WordPress 6.4)
 -->

*   `featured`
*   `about`
*   `audio` (WordPress 6.4で追加)
*   `banner`
*   `buttons`
*   `call-to-action`
*   `columns`
*   `contact`
*   `footer`
*   `gallery`
*   `header`
*   `media`
*   `portfolio`
*   `posts`
*   `query` (代わりに `posts` を使用する)
*   `services`
*   `team`
*   `testimonials`
*   `text`
*   `video` (WordPress 6.4で追加)

<!-- 
It’s generally best to use these default categories for your theme. This keeps a consistent UI that users will be accustomed to. But there are times when you may want to add your own categories or even remove those that are already registered.
 -->

あなたのテーマには、通常はこれらのデフォルト・カテゴリーを使用するのが最適です。これにより、ユーザーが慣れ親しんだ一貫した UI を維持できます。ただし、あなた独自カテゴリーを追加したり、すでに登録されているカテゴリーを削除したい場合もあります。

<!-- 
In this section of the article, you’ll learn how to both register and unregister custom block pattern categories.
 -->

本稿のこのセクションでは、カスタム・ブロック・パターン・カテゴリーの登録と解除の両方を学ぶことができます。

<!-- 
### Registering a pattern category
 -->

### パターン・カテゴリーの登録

<!-- 
To register a custom category for putting one or more of your patterns into, you must use the [`register_block_pattern_category()`](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) function:
 -->

1つ以上のパターンを格納するためのカスタム・カテゴリーを登録するには、[`register_block_pattern_category()`](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) 関数を使用する必要があります:

```php
register_block_pattern_category( 
	string $category_name, 
	array $category_properties 
): bool
```

<!-- 
The function accepts two parameters:
 -->

この関数は、2つのパラメータを受け取ります:

<!-- 
*   **`$category_name`:** A unique ID/slug for the category. It’s good practice to prefix this with your theme slug.
*   **`$category_properties`:** An array of properties for defining further data about the category:
    *   **`label`:** A human-readable label/title for the category that may be translated.
    *   **`description`:** A description for the category that may be translated.
 -->

*   **`$category_name`:** カテゴリー用の一意の ID/スラッグです。あなたのテーマのスラッグを接頭辞として付けるのは、良い習慣です。
*   **`$category_properties`:** カテゴリーに関する追加のデータを定義するための、プロパティの配列です:
    *   **`label`:** 翻訳可能な、カテゴリー用の人間可読ラベル/タイトルです。
    *   **`description`:** 翻訳可能な、カテゴリー用の説明です。

<!-- 
Try adding a new custom pattern category for your theme. Add this code to your theme’s `functions.php` file:
 -->

あなたのテーマ用に、新規カスタム・パターン・カテゴリーを追加してみましょう。あなたのテーマの `functions.php` ファイルに以下のコードを追加します:

```php
add_action( 'init', 'themeslug_register_pattern_categories' );

function themeslug_register_pattern_categories() {
	register_block_pattern_category( 'themeslug/custom', array( 
		'label'       => __( 'Theme Name: Custom', 'themeslug' ),
		'description' => __( 'Custom patterns for Theme Name.', 'themeslug' )
	) );
}
```

<!-- 
Now try adding the `themeslug/custom` category to any block pattern:
 -->

では、任意のブロック・パターンに `themeslug/custom` カテゴリーを追加してみましょう:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured, themeslug/custom
 */
?>
<!-- Your block markup goes here. -->
```

<!-- 
Any registered patterns for this category will now appear in the inserter and under **Appearance > Editor > Patterns**:
 -->

このカテゴリーに登録された任意のパターンは、インサーター内と **外観 > エディター > パターン** 以下に表示されます:

<!-- 
[![Custom pattern category showing a single pattern in the WordPress Patterns library.](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-category.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-category.jpg?ssl=1)
 -->

[![WordPress パターン・ライブラリ内に1つのパターンを表示する、カスタム・パターン・カテゴリー。](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-category.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/patterns-category.jpg?ssl=1)

<!-- 
### Unregistering a pattern category
 -->

### パターン・カテゴリーの登録解除

<!-- 
To unregister a registered pattern category, you must use the [`unregister_block_pattern_category()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern_category/) function:
 -->

登録済みのパターン・カテゴリーを登録解除するには、[`unregister_block_pattern_category()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern_category/) 関数を使用する必要があります:

```php
unregister_block_pattern_category( string $category_name ): bool
```

<!-- 
The function accepts a single parameter:
 -->

この関数は、単一のパラメータを受け付けます:

<!-- 
*   **`$category_name`:** The name (i.e., slug) of the registered category to unregister.
 -->

*   **`$category_name`:** 登録解除する登録カテゴリーの、名前 (つまり、スラッグ) です。

<!-- 
Try adding this code to your `functions.php` to remove the `themeslug/custom` category you registered in the previous step:
 -->

このコードをあなたの `functions.php` に追加して、前の手順で登録した `themeslug/custom` カテゴリーを削除してみましょう:

```php
add_action( 'init', 'themeslug_unregister_pattern_categories' );function themeslug_unregister_pattern_categories() {	unregister_block_pattern_category( 'themeslug/custom' );}
```