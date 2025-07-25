<!-- 
# Registering Patterns
 -->

# パターンの登録

<!-- 
In [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/), you learned how to create patterns from the WordPress admin interface. Now it’s time to learn how to add these custom patterns directly to your theme
 -->

[パターン入門](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/) では、WordPress 管理インターフェースからパターンを追加する方法を学びました。今度は、これらのカスタム・パターンをあなたのテーマに直接追加する方法を学びましょう。

<!-- 
This article will show you how to take a pattern’s block code and register it with WordPress from within your theme. It will also cover unregistering patterns and registering/unregistering pattern categories.
 -->

本稿では、あなたのテーマの中からパターンのブロック・コードを取り出し、WordPress に登録する方法を紹介します。また、パターンの登録解除やパターン・カテゴリーの登録/登録解除についても説明します。

<!-- 
## Creating patterns
 -->

## パターンの制作

<!-- 
If you’re unfamiliar with creating custom patterns, take a moment to study the [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) guide, which will walk you through the process.
 -->

カスタム・パターンの制作に慣れていない人は、手順を説明した [パターン入門](https://developer.wordpress.org/themes/patterns/registering-patterns/) ガイドをご一読ください。

<!-- 
Your pattern can be anything you like, but for the purposes of this article, the code shared below will be of a core Cover block with some blocks nested within it, following this structure:
 -->

あなたの好きなパターンでかまいませんが、本稿の趣旨から、以下のコードでは、コア「カバー」ブロックと、その中にネストされたいくつかのブロックを、以下の構造に従って紹介します:

<!-- 
*   Group
    *   Heading
    *   Paragraph
    *   Buttons
        *   Button
 -->

*   グループ
    *   見出し
    *   段落
    *   ボタン
        *   ボタン

<!-- 
Feel free to try recreating this yourself from the editor, especially if you are just getting used to working with the editor. Here is a screenshot of the pattern from the editor:
 -->

特にエディターでの作業に慣れていない人は、エディターから自身で自由にこれを再現してみてください。以下はエディターからのパターンのスクリーンショットです:

<!-- 
[![WordPress pattern editor that shows a basic Cover block with a black background and white demo text in the content area.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?ssl=1)
 -->

[![コンテンツ・エリアに黒の背景と白のデモ・テキストを使った、基本的な「カバー」ブロックを表示している WordPress パターン・エディター。](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?ssl=1)

<!-- 
You can also customize this however you like, but it’s recommended to keep this relatively simple for your first time creating a pattern.
 -->

これも好きなようにカスタマイズできますが、初めてパターンを制作する場合は、比較的シンプルにしておくことをおすすめします。

<!-- 
Here is what the above pattern’s block markup looks like (read the [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/) article for more information on getting pattern code):
 -->

上記のパターンのブロック・マークアップは、以下のようになります (パターン・コードの取得に関する詳細情報は、[パターン入門](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/) 記事をご覧あれ):

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
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →︎</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
For the remainder of this article, you will work with this same pattern, learning how to register it, unregister it, and customize it further.
 -->

本稿の残りの部分では、この同じパターンを使って、登録、登録解除、さらにカスタマイズする方法を学びます。

<!-- 
It’s good practice to wrap most patterns in a Group, Cover, or other container block (i.e., a block that allows nested blocks). This makes it easier for your theme users to move the entire pattern around in the editor. You can also add a CSS class to this outer block for any custom styling that applies to the entire pattern.
 -->

ほとんどのパターンを「グループ」「カバー」などのコンテナ・ブロック (つまり、入れ子ブロックが可能なブロック) で囲むのは良い慣習です。こうすることで、あなたのテーマのユーザーが、エディター内でパターン全体を移動しやすくなります。また、この外側のブロックに CSS クラスを追加することで、パターン全体に適用されるカスタム・スタイルを指定できます。

<!-- 
## Registering patterns
 -->

## パターンの登録

<!-- 
There are two methods for registering block patterns in WordPress:
 -->

WordPress でブロック・パターンを登録するには、2つの方法があります:

<!-- 
*   By placing files with block markup in them into the /patterns folder in your theme.
*   By manually calling the `register_block_pattern()` function.
 -->

*   あなたのテーマの /patterns フォルダー内に、ブロック・マークアップを含むファイルの配置。
*   `register_block_pattern()` 関数の、手動コール。

<!-- 
The most straightforward route is the first. You’ll learn how to do both in the next sections, but this handbook will recommend using the `/patterns` folder except in some edge cases.
 -->

最も簡単なのは最初の方法です。次のセクションではどちらの方法も学びますが、本ハンドブックでは一部の例外的なケースを除き、`/patterns` フォルダーの利用を推奨します。

<!-- 
### Using the /patterns directory to register patterns
 -->

### /patterns ディレクトリを使った、パターンの登録

<!-- 
WordPress will recognize any pattern file placed in your theme’s `/patterns` folder, and it will automatically register it for you, provided that it has a valid pattern file header.
 -->

WordPress は、あなたのテーマの `/patterns` フォルダーに置かれたパターン・ファイルを認識し、それが有効なパターン・ファイル・ヘッダーを持っている限り、自動的にあなたのためにそれを登録します。

<!-- 
A [file header](https://codex.wordpress.org/File_Header) is PHP-commented code with a list of key + value pairs at the top of a file. WordPress parses this information to gather metadata. In this case, the metadata is used to register a block pattern.
 -->

[ファイル・ヘッダー](https://codex.wordpress.org/File_Header) とは、ファイルの先頭にキー・バリューペアのリストを持つ、PHP でコメントされたコードのことです。WordPress はこの情報を解析してメタデータを収集します。この場合、メタデータはブロック・パターンを登録するために使用されます。

<!-- 
For pattern file headers, these are the keys that you can set:
 -->

パターン・ファイル・ヘッダーの場合、設定できるキーは以下の通りです:

<!-- 
*   **`Title`:** A human-readable title that can be translated.
*   **`Slug`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`Categories`:** A comma-separated list of categories in which the pattern belongs.
*   **`Description`:** The long description of the registered pattern. Only shown to screen readers.
*   **`Viewport Width`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
*   **`Inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
*   **`Keywords`:** A comma-separated list of keywords related to the pattern. Used when a user searches in the inserter.
*   **`Block Types`:** A comma-separated list of block types to associate the pattern with (e.g., `core/cover`, `core/post-content`).
*   **`Post Types`:** A comma-separated list of post types in which to limit the pattern (e.g., `post`, `page`). Defaults to all post types.
*   **`Template Types`:** A comma-separated list of template types the pattern fits with (e.g., `home`, `single`).
 -->

*   **`Title`:** 翻訳可能で、人間可読な、タイトルです。
*   **`Slug`:** `namespace/pattern-name` の形で、あなたのパターンに固有の、名前空間スラッグです。
*   **`Categories`:** パターンが属するカテゴリーの、カンマ区切りリストです。
*   **`Description`:** 登録されたパターンの、長い説明です。スクリーンリーダーにのみ表示されます。
*   **`Viewport Width`:** パターンをプレビュー表示する際の、`<iframe>` ビューポートの幅 (ピクセル単位) です。
*   **`Inserter`:** インサーターに、パターンを表示するか否かです。デフォルトは `true` です。
*   **`Keywords`:** パターンに関連するキーワードの、カンマ区切りリストです。ユーザーがインサーターで検索する際に、使用されます。
*   **`Block Types`:** パターンを関連付ける、ブロック・タイプのカンマ区切りリストです (例: `core/cover`、`core/post-content`)。
*   **`Post Types`:** パターンを限定する、投稿タイプのカンマ区切りリストです (例: `post`、`page`)。デフォルトはすべての投稿タイプです。
*   **`Template Types`:** パターンが適合する、テンプレート・タイプのカンマ区切りリストです (例: `home`、`single`)。

<!-- 
For most patterns, you should at least add the Title, Slug, and Categories fields. Pattern files should look like this:
 -->

ほとんどのパターンでは、少なくとも Title、Slug、Categories フィールドを追加する必要があります。パターン・ファイルは以下のようになります:

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

前のセクションでコピーしたコードを、あなたのテーマの `/patterns/hero.php` ファイルに追加しましょう:

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
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →︎</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

<!-- 
Now if you add or edit a new post in WordPress, you should see your pattern listed in the inserter. Click the **Patterns** tab and select **Featured**:
 -->

これで、WordPress で新規投稿を追加または編集すると、インサーターにパターンが表示されるはずです。**パターン** タブをクリックし、**注目** を選択します:

<!-- 
[![WordPress post editor with the Patterns inserter open. The Featured sub-panel is selected and shows a single pattern.](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?ssl=1)
 -->

[![パターン・インサーターが開いている、WordPress 投稿エディター。「Featured (注目)」サブパネルが選択され、1つのパターンが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?ssl=1)

<!-- 
You should also be able to see your pattern listed under **Appearance > Editor > Patterns** in the WordPress admin.
 -->

また、WordPress 管理画面の **外観 > エディター > パターン** 以下に、あなたのパターンが表示されているはずです。

<!-- 
### Using PHP to register patterns
 -->

### PHP を使った、パターンの登録

<!-- 
Instead of using the `/patterns` folder to auto-register your patterns, you may choose to manually register them via PHP. You can mix and match both registration methods, but an individual pattern must be registered with only one method.
 -->

`/patterns` フォルダーを使ってパターンを自動登録する代わりに、PHP 経由でパターンを手動登録できます。どちらの登録方法も混在させることができますが、個々のパターンはどちらかの方法で登録しなければなりません。

<!-- 
To register block patterns with PHP, you must use the [`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) function. Here is what its signature looks like:
 -->

PHP でブロック・パターンを登録するには、[`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) 関数を使用する必要があります。そのシグネチャは以下のようになります:

```php
register_block_pattern( 
	string $pattern_name, 
	array $pattern_properties 
): bool
```

<!-- 
The function accepts two parameters and returns `true` or `false`, depending on whether the pattern was successfully registered:
 -->

この関数は2つのパラメータを受け取り、パターンが正常に登録されたかどうかに応じて、`true` または `false` を返します:

<!-- 
*   **`$pattern_name`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`$pattern_properties`:**
    *   **`content`:** The block markup for the pattern.
    *   **`title`:** A human-readable title that can be translated.
    *   **`categories`:** An array of categories in which the pattern belongs.
    *   **`description`:** The long description of the registered pattern. Only shown to screen readers.
    *   **`viewportWidth`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
    *   **`inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
    *   **`keywords`:** An array of keywords related to the pattern. Used when a user searches in the inserter.
    *   **`blockTypes`:** An array of block types to associate the pattern with.
    *   **`postTypes`:** An array of post types in which to limit the pattern. Defaults to all post types.
    *   **`source`:** The source for the registered pattern. This should be set to `theme` since the pattern is coming from a theme.
    *   **`templateTypes`:** An array of template types the pattern fits with.
 -->

*   **`$pattern_name`:** `namespace/pattern-name` の形をした、あなたのパターン固有の名前空間スラッグです。
*   **`$pattern_properties`:**
    *   **`content`:** そのパターンのブロック・マークアップです。
    *   **`title`:** 翻訳可能な、人間可読なタイトルです。
    *   **`categories`:** そのパターンが属する、カテゴリーの配列です。
    *   **`description`:** 登録されたパターンの長い説明です。スクリーンリーダーにのみ表示されます。
    *   **`viewportWidth`:** そのパターンをプレビューする際の、`<iframe>` ビューポートの幅 (ピクセル単位) です。
    *   **`inserter`:** そのパターンをインサーターに表示するか否かです。デフォルトは、`true` です。
    *   **`keywords`:** そのパターンに関連する、キーワードの配列です。ユーザーがインサーターで検索する際に使用されます。
    *   **`blockTypes`:** そのパターンを関連付ける、ブロック・タイプの配列です。
    *   **`postTypes`:** そのパターンに限定する、投稿タイプの配列です。デフォルトは、すべてのポストタイプです。
    *   **`source`:** 登録されたパターンのソースです。パターンはテーマに由来しているため、`theme` に設定する必要があります。
    *   **`templateTypes`:** そのパターンに適合するテンプレート・タイプの配列です。

<!-- 
When registering patterns via PHP, you should do so on the `init` hook. Now try registering your custom pattern by adding this code in `functions.php` (be sure to add your custom markup to the `content` property):
 -->

PHP 経由でパターンを登録する際は、`init` フックで行う必要があります。では、`functions.php` に次のコードを追加して、あなたのカスタム・パターンを登録してみてください ( `content` プロパティに、あなたのカスタム・マークアップを必ず追加すること):

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
### Conditionally registering patterns
 -->

### パターンの条件付き登録

<!-- 
If you need to conditionally register an entire pattern, there are two methods to choose from, depending on how you prefer to register patterns.
 -->

パターン全体を条件付きで登録する必要がある場合、パターンをどのように登録したいかによって、2つの方法から選択できます。

<!-- 
#### Conditionally registering patterns in the /patterns folder
 -->

#### /patterns フォルダーに、パターンの条件付き登録

<!-- 
If you have used the auto-registration method of placing your pattern in your theme’s `/patterns` folder, there is no true way to conditionally register it. What you must do in this case is unregister the pattern.
 -->

あなたのテーマの `/patterns` フォルダーにあなたのパターンを配置する自動登録法を使用した場合、それを条件付きで登録する真の方法はありません。この場合しなければならないのは、パターンの登録を解除することです。

<!-- 
Suppose that you wanted to only make the hero pattern you registered earlier available if the `core/paragraph` block is registered. In a real-world scenario, you’d likely be checking for a third-party block, and the `core/paragraph` block is used only for the sake of this example.
 -->

あなたが以前に登録した hero パターンを、`core/paragraph` ブロックが登録されている場合にのみ有効化したいとします。実際のシナリオでは、サードパーティのブロックをチェックすることが多いでしょう。`core/paragraph` ブロックは、この例のためだけに使用しています。

<!-- 
Try this code inside of your `functions.php` file to unregister your previously-registered pattern:
 -->

あなたの `functions.php` ファイルの中でこのコードを試して、以前に登録したパターンの登録を解除してください:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) {
		unregister_block_pattern( 'themeslug/hero' );
	}
}
```

<!-- 
The above code uses the [`WP_Block_Type_Registry`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/) class, which stores all block types that are registered on the server-side with WordPress. Using the class’s [`is_registered()`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/is_registered/) method, you can determine whether a block is registered.
 -->

上記のコードでは、WordPress にサーバーサイドで登録されているすべてのブロック・タイプを格納する [`WP_Block_Type_Registry`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/) クラスを使用しています。このクラスの [`is_registered()`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/is_registered/) メソッドを使うことで、ブロックが登録されているかどうかを判断できます。

<!-- 
#### Conditionally registering patterns via [register\_block\_pattern()](https://developer.wordpress.org/reference/functions/register_block_pattern/)
 -->

#### [register\_block\_pattern()](https://developer.wordpress.org/reference/functions/register_block_pattern/) 経由の条件付きパターン登録

<!-- 
If you manually registered your patterns via PHP, you only need to wrap your call to `register_block_pattern()` with your conditional check.
 -->

PHP 経由であなたのパターンを手動で登録した場合、`register_block_pattern()` へのあなたのコールを、あなたの条件付きチェックでラップするだけで良いのです。

<!-- 
Using the same example as above, try only registering your pattern if the `core/paragraph` block is registered by adding this to `functions.php`:
 -->

上記と同じ例で、これを `functions.php` に追加することで、`core/paragraph` ブロックが登録されている場合、あなたのパターンを登録することのみを試してみましょう:

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
## Unregistering patterns
 -->

## パターンの登録解除

<!-- 
There are times when you need to unregister block patterns so that they do not appear in the inserter for users. For example, you may want to remove some of the core WordPress patterns, those added by a parent theme (if you’re building a child theme), or those added by third-party plugins.
 -->

ブロック・パターンの登録を解除する必要があるときがあり、そうすることで、ユーザーに対してブロック・パターンがインサーターに表示されないようにできます。たとえば、WordPress コアパターン、(子テーマを構築している場合) 親テーマによって追加されたパターン、サードパーティのプラグインによって追加されたパターンなどを削除したい場合があります。

<!-- 
When you need to unregister a single block pattern, you’ll use the [`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) function:
 -->

単一のブロック・パターンを登録解除する必要がある場合は、[`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) 関数を使用します:

```php
unregister_block_pattern( string $pattern_name ): bool
```

<!-- 
Like when registering patterns, you’ll also want to unregister on the `init` hook. Because patterns are generally (but not always) registered with the default priority `10` on `init`, you’ll want to use a higher priority so that your code runs later.
 -->

パターンを登録する際同様、`init` フックでも登録解除したいでしょう。パターンは一般的に (常にではないが) デフォルトの優先度 `10` で `init` に登録されるため、あなたのコードが後で実行されるように、より高い優先度を使いたいでしょう。

<!-- 
Try unregistering your custom pattern from earlier by adding this code to your `functions.php` file:
 -->

あなたの `functions.php` ファイルに次のコードを追加することで、先ほどのあなたのカスタム・パターンを登録解除してみましょう:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	unregister_block_pattern( 'themeslug/hero' );
}
```

<!-- 
### Removing Core patterns
 -->

### 「コア」パターンの除去

<!-- 
While you can use `unregister_block_pattern()` to unregister individual core WordPress patterns, you can also choose to get rid of all of them by removing support for the core-block-patterns feature.
 -->

`unregister_block_pattern()` を使って個々のコア WordPress パターンを登録解除できるが、コア・ブロック・パターン機能への対応を解除することでも、すべてのパターンを削除できます。

<!-- 
To remove all core WordPress patterns, add this code to your theme’s `functions.php` file:
 -->

WordPress のコア・パターンをすべて削除するには、あなたのテーマの `functions.php` ファイルに次のコードを追加します:

```php
add_action( 'after_setup_theme', 'themeslug_remove_core_patterns' );

function themeslug_remove_core_patterns() {
	remove_theme_support( 'core-block-patterns' );
}
```

<!-- 
### Disabling remote patterns
 -->

### 「リモート」パターンの無効化

<!-- 
WordPress also automatically loads some patterns remotely from the official [Pattern Directory](https://wordpress.org/patterns/) on WordPress.org. There are some situations where you might not want to load these patterns, such as when they don’t match your theme design. You may also want to opt out of calling a remote API on a site that you’re building for a client. Whatever the case, you can disable this by filtering the [`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) hook.
 -->

WordPress はまた、WordPress.org の公式 [パターン・ディレクトリー](https://wordpress.org/patterns/) からいくつかのパターンをリモートで自動的にロードします。これらのパターンがあなたのテーマ設計に合致しない場合など、ロードしたくない状況もあるでしょう。また、クライアントのために構築しているサイトで、リモート API をコールしないようにしたい場合もあるでしょう。どのような場合でも、[`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) フックをフィルタリングすることで、これを無効にできます。

<!-- 
To disable remote patterns, add this code to your `functions.php` file:
 -->

リモート・パターンを無効にするには、あなたの `functions.php` に次のコードを追加します:

```php
add_filter( 'should_load_remote_block_patterns', '__return_false' );
```

<!-- 
## Pattern categories
 -->

## パターン・カテゴリー

<!-- 
WordPress has several block pattern categories that it registers by default:
 -->

WordPress には、デフォルトで登録されているブロック・パターンのカテゴリーがいくつかあります:

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
*   `query` (代わりに `posts` を使用)
*   `services`
*   `team`
*   `testimonials`
*   `text`
*   `video` (WordPress 6.4で追加)

<!-- 
It’s generally best to use these default categories for your theme. This keeps a consistent UI that users will be accustomed to. But there are times when you may want to add your own categories or even remove those that are already registered.
 -->

一般的に、あなたのテーマにはこれらのデフォルト・カテゴリーを使用するのがベストです。それによって、ユーザーが慣れ親しんだ一貫した UI を保つことができます。しかし、独自のカテゴリーを追加したり、すでに登録されているカテゴリーを削除したい場合もあるでしょう。

<!-- 
In this section of the article, you’ll learn how to both register and unregister custom block pattern categories.
 -->

このセクションでは、カスタム・ブロック・パターンのカテゴリーを登録する方法と登録解除する方法の両方を学びます。

<!-- 
### Registering a pattern category
 -->

### パターン・カテゴリーの登録

<!-- 
To register a custom category for putting one or more of your patterns into, you must use the [`register_block_pattern_category()`](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) function:
 -->

あなたのパターンを1つ以上入れるためのカスタム・カテゴリーを登録するには、[`register_block_pattern_category()`](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) 関数を使用する必要があります:

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
*   **`$category_name`:** A unique ID/slug for the category. It’s good practice to prefix this with your theme slug (e.g., `themeslug-category-name`).
*   **`$category_properties`:** An array of properties for defining further data about the category:
    *   **`label`:** A human-readable label/title for the category that may be translated.
    *   **`description`:** A description for the category that may be translated.
 -->

*   **`$category_name`:** カテゴリー用の一意の ID/スラッグです。あなたのテーマのスラッグを接頭辞としてつけるとよいでしょう (例: `themeslug-category-name`)。
*   **`$category_properties`:** カテゴリーに関する詳細なデータを定義するための、プロパティの配列です:
    *   **`label`:** 翻訳される可能性のあるカテゴリーの、人間可読なラベル/タイトルです。
    *   **`description`:** 翻訳される可能性のあるカテゴリーの、説明です。

<!-- 
Try adding a new custom pattern category for your theme. Add this code to your theme’s `functions.php` file:
 -->

あなたのテーマに新規カスタム・パターン・カテゴリーを追加してみてください。あなたのテーマの `functions.php` ファイルにこのコードを追加してください:

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

では、任意のブロック・パターンに `themeslug/custom` カテゴリーを加えてみましょう:

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
Any registered patterns for this category will now appear in the inserter and under **Appearance > Editor > Patterns** (**Appearance > Patterns** for classic themes):
 -->

このカテゴリーに登録されたパターンは、インサーターと **外観 > エディター > パターン** (クラシック・テーマの場合は、**外観 > パターン** ) 以下に表示されます:

<!-- 
[![WordPress Pattern library in the Site Editor. It shows a custom category selected, which has a single pattern preview.](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?ssl=1)
 -->

[![サイト・エディターの WordPress パターン・ライブラリ。選択されたカスタム・カテゴリーが表示され、単一のパターンがプレビューされる。](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?ssl=1)

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

この関数は、単一のパラメータを受け取ります:

<!-- 
*   **`$category_name`:** The name (i.e., slug) of the registered category to unregister.
 -->

*   **`$category_name`:** 登録解除する登録カテゴリーの名前 (つまり、スラッグ) です。

<!-- 
Try adding this code to your `functions.php` to remove the `themeslug/custom` category you registered in the previous step:
 -->

このコードをあなたの `functions.php` に追加して、前ステップで登録した `themeslug/custom` カテゴリーを削除してみましょう:

```php
add_action( 'init', 'themeslug_unregister_pattern_categories' );

function themeslug_unregister_pattern_categories() {
	register_block_pattern_category( 'themeslug/custom' );
}
```