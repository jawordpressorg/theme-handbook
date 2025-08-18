<!-- 
# Block Variations
 -->

# ブロック・バリエーション

<!-- 
The Block Variations API is a powerful feature that allows you to extend any registered blocks. Basically, it gives you the ability to create alternate versions of a block’s settings. This can make it easier for your users to insert blocks without the hassle of going through all of the setup they might need for a specific scenario.
 -->

ブロック・バリエーション API は、任意の登録済みブロックを拡張できる強力な機能です。基本的には、ブロックの設定の代替バージョンを制作する機能を提供します。これにより、あなたのユーザーは、特定のシナリオで必要なセットアップをすべて実施する手間を省き、ブロックを挿入しやすくなります。

<!-- 
The [Block Variations API](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-variations/) is often pitched as a plugin developer API. In many cases, plugins are the best place for variations to live. But there are also use cases for theme creators.
 -->

[ブロック・バリエーション API](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-variations/) は、プラグイン開発者向けの API としてよく紹介されています。多くのケースでは、プラグインがバリエーションを実装する最適な場所です。ただし、テーマ作者向けのユースケースも存在します。

<!-- 
Several WordPress features use the term “variations” in their name. This can be confusing at times. The biggest thing to note is that block variations are not the same thing as [global style variations](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/) and [block style variations](https://developer.wordpress.org/themes/features/block-style-variations/).
 -->

WordPress のいくつかの機能では、名称の中に「バリエーション」という用語が使用されています。これは時々混乱を招くことがあります。最も重要な点は、ブロック・バリエーションは [グローバル・スタイル・バリエーション](https://developer.wordpress.org/themes/global-settings-and-styles/style-variations/) や [ブロック・スタイル・バリエーション](https://developer.wordpress.org/themes/features/block-style-variations/) とは異なる点です。

<!-- 
## What are block variations?
 -->

## ブロック・バリエーションって ?

<!-- 
The simplest explanation of block variations is that they are literally variations on an existing block. Let’s take a look at an example to explore this further.
 -->

ブロック・バリエーションの最もシンプルな説明は、既存のブロックの文字通りのバリエーションであるということです。例を見て、さらに詳しく説明しましょう。

<!-- 
The Social Icon block is a simple block to add a link to some social site, but WordPress bundles many different variations of this base block to cover a wide range of social sites:
 -->

「ソーシャル・アイコン」ブロックは、ソーシャル・サイトへのリンクを追加するための、シンプルなブロックですが、WordPress は、さまざまなソーシャル・サイトに対応するために、この基本ブロックのさまざまなバリエーションをバンドルしています:

<!-- 
[![WordPress post editor with several social icons shown in a row.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-variations-social-icons.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-variations-social-icons.jpg?ssl=1)
 -->

[![複数のソーシャル・アイコンが横一列に表示されている、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-variations-social-icons.jpg?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-variations-social-icons.jpg?ssl=1)

<!-- 
Without the Block Variations API, each of those variations would need to be individually-coded blocks. There are many reasons that would be a bad idea. So instead of writing a block for each social icon, developers only need to make a few configuration changes to create an alternate version of the original block.
 -->

ブロック・バリエーション API がなければ、それらのバリエーションは、それぞれ個別にコードされたブロックとして実装する必要がありました。多くの理由から、それは悪いアイデアです。そのため、各ソーシャル・アイコンごとにブロックを作成する代わりに、開発者は、元のブロックの代替バージョンを作成するために、いくつかの設定変更を実行するだけなのです。

<!-- 
There are many, many ways that you could potentially change a block to make it different from its default configuration. This can be something as simple as setting up a Spacer block with your theme’s preferred default spacing. Or it can be as complex as a custom Query Loop block with a complex posts query for the front-page template. 
 -->

ブロックをそのデフォルト設定から異なるものに変更する方法は、非常に多くの可能性があります。これは、あなたのテーマの好みのデフォルトの余白を設定するだけの、シンプルな「スペーサー」ブロックのセットアップかもしれません。または、フロントページ・テンプレート用の複雑な投稿クエリーを含む、カスタム「クエリー・ループ」ブロックのように複雑なものでもあります。

<!-- 
While it is more advanced than some theme features, the API does give you the flexibility to make more complex themes than what is available out of the box.
 -->

一部のテーマ機能よりも高度な機能を備えていますが、API は、標準で提供されているものよりも複雑なテーマを作成する柔軟性を提供します。

<!-- 
### Block variations vs. block styles
 -->

### ブロック・バリエーション 対 ブロック・スタイル

<!-- 
An oft-repeated question is: *When should I create a block variation vs. a block style?*
 -->

繰り返しよく聞かれる質問は: *いつブロック・バリエーションを制作するべきで、いつブロック・スタイルを制作するべき ?*

<!-- 
The answer is almost always the same as the answer to another question: *Can these changes be made through* [*`theme.json` styles*](https://developers.wordpress.org/themes/global-settings-and-styles/styles/) *or CSS?* If yes, you should almost always create a custom [block style](https://developers.wordpress.org/themes/features/block-style-variations/).
 -->

その答えは、別の質問の答えとほぼ同じです: *これらの変更は、* [*`theme.json` スタイル*](https://developers.wordpress.org/themes/global-settings-and-styles/styles/) *または CSS を通じて行うことができますか ?* Yes の場合には、ほぼ常にカスタム [ブロック・スタイル](https://developers.wordpress.org/themes/features/block-style-variations/) を作成すべきです。

<!-- 
But if you need to change a block’s settings so that it is set up differently when a user inserts an instance of it into a post, a custom block variation is probably the best route to take.
 -->

ただし、ブロックの設定を変更する必要がある場合には、異なる設定に設定する必要があり、ユーザーが投稿にそのインスタンスを挿入する際には、カスタム・ブロック・バリエーションが最適な選択肢となるでしょう。

<!-- 
## Working with block variations
 -->

## ブロック・バリエーションの取り扱い

<!-- 
Block variations require that you work with JavaScript instead of PHP. The examples below do not require a build process, so you can use them as-is.
 -->

ブロック・バリエーションを使用するには、PHP ではなく JavaScript を使用する必要があります。以下の例は、ビルド・プロセスを必要としないため、そのまま使用できます。

<!-- 
But the more you work with WordPress’ JavaScript packages, the more likely you’ll want to incorporate build tools into your workflow. It’s possible to use the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package, originally meant block development, with your theme. For a deeper dive into how this works, read [Beyond block styles, part 1: using the WordPress scripts package with themes](https://developer.wordpress.org/news/2023/07/beyond-block-styles-part-1-using-the-wordpress-scripts-package-with-themes/).
 -->

しかし、WordPress の JavaScript パッケージを扱うほど、あなたのワークフローにビルド・ツールを取り入れたいと思うようになるでしょう。もともとブロック開発を目的とした [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) パッケージを、あなたのテーマで使うことも可能になります。このしくみについて詳しく知りたい人は、[ブロック・スタイルを超えて、パート1: テーマで WordPress スクリプト・パッケージを使用](https://developer.wordpress.org/news/2023/07/beyond-block-styles-part-1-using-the-wordpress-scripts-package-with-themes/) をご覧ください。

<!-- 
In the next sections, you will learn how to work with block variations by building a simple variation on the WordPress Spacer block, as shown in this screenshot:
 -->

次のセクションでは、このスクリーンショットに示すように、WordPress の「スペーサー」ブロックに簡単なバリエーションを構築することで、ブロック・バリエーションの扱い方を学びます:

<!-- 
[![WordPress post editor with a Table of Contents block, Spacer block, and demo content.](https://i0.wp.com/developer.wordpress.org/files/2023/10/variation-theme-spacer.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/variation-theme-spacer.jpg?ssl=1)
 -->

[![「目次」ブロック、「スペーサー」ブロック、デモ・コンテンツを備えた WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/variation-theme-spacer.jpg?resize=2048%2C1072&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/variation-theme-spacer.jpg?ssl=1)

<!-- 
For a deeper dive into block variations, check out these tutorials on the WordPress Developer Blog:
 -->

ブロック・バリエーションについてさらに詳しく知りたい人は、WordPress 開発者ブログの以下のチュートリアルをご覧ください:

<!-- 
*   [An introduction to block variations](https://developer.wordpress.org/news/2023/08/an-introduction-to-block-variations/)
*   [Building a book review grid with a Query Loop block variation](https://developer.wordpress.org/news/2022/12/building-a-book-review-grid-with-a-query-loop-block-variation/)
 -->

*   [ブロック・バリエーションの概要](https://developer.wordpress.org/news/2023/08/an-introduction-to-block-variations/)
*   [「クエリー・ループ」ブロック・バリエーションを使用して、書籍レビュー・グリッドの構築](https://developer.wordpress.org/news/2022/12/building-a-book-review-grid-with-a-query-loop-block-variation/)

<!-- 
### Setup: Loading JavaScript
 -->

### セットアップ: JavaScript のロード

<!-- 
The first step for working with block variations is to create an empty file for adding your custom JavaScript to. This can be at any location you choose, but the code example below will attempt to find a `block-variations.js` in your theme’s `/assets/js` folder.
 -->

ブロック・バリエーションを扱う最初のステップは、あなたのカスタム JavaScript を追加するための、空ファイルを作成することです。このファイルは任意の場所に作成できますが、以下のコード例は、あなたのテーマの `/assets/js` フォルダー内で `block-variations.js` を検索します。

<!-- 
So your theme structure should look similar to this:
 -->

したがって、あなたのテーマ構造は、以下のようなものに類似しています:

<!-- 
*   `/assets`
    *   `/js`
        *   `/block-variations.js`
*   …other files and folders
 -->

*   `/assets`
    *   `/js`
        *   `/block-variations.js`
*   …その他のファイルとフォルダー

<!-- 
To load that file in the editor, you must call the [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) function within a callback added to the [`enqueue_block_editor_assets`](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) action hook.
 -->

そのファイルをエディターにロードするには、[`enqueue_block_editor_assets`](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) アクション・フックに追加されたコールバック内で、[`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) 関数をコールする必要が あります。

<!-- 
Add this code to your theme’s `functions.php` file:
 -->

このコードを、あなたのテーマの `functions.php` ファイルに追加してください:

```php
add_action( 'enqueue_block_editor_assets', 'themeslug_enqueue_block_variations' );

function themeslug_enqueue_block_variations() {
	wp_enqueue_script(
		'themeslug-block-variations',
		get_theme_file_uri( 'assets/js/block-variations.js' ),
		array( 
			'wp-blocks', 
			'wp-dom-ready',
			'wp-i18n'
		),
		wp_get_theme()->get( 'Version' ),
		true
	);
}
```

<!-- 
Take note of the dependencies array (third parameter) within `wp_enqueue_script()`. This includes the `wp-blocks`, `wp-dom-ready`, and `wp-i18n` scripts, which are needed for the JavaScript code in the below examples.
 -->

`wp_enqueue_script()` 内の依存関係の配列 (3番目のパラメータ) に注意してください。これには、以下の例における JavaScript コードに必要な `wp-blocks`、`wp-dom-ready`、および `wp-i18n` スクリプトが含まれます。

<!-- 
### Registering block variations
 -->

### ブロック・バリエーションの登録

<!-- 
To register block variations, you must use the `registerBlockVariation()` JavaScript function. Here is a look at the function’s signature:
 -->

ブロック・バリエーションを登録するには、JavaScript `registerBlockVariation()` 関数を使用する必要があります。以下に、関数のシグネチャを示します:

```javascript
const registerBlockVariation = ( blockName, variation )
```

<!-- 
The function accepts two parameters:
 -->

この関数は2つのパラメータを受け取ります:

<!-- 
*   **`blockName`:** The name of the block (including namespace) to register the variation for.
*   **`variation`:** An optional object for configuring the variation, which may include any of the following properties:
    *   **`name`:** A unique, machine-readable slug for your variation.
    *   **`title`:** A human-readable title for your variation that should be internationalized.
    *   **`description`:** A human-readable description of the variation that should be internationalized if added.
    *   **`category`:** The slug of a registered block type category
    *   **`keywords`:** An array of keywords to help users discover the variation when searching.
    *   **`icon`:** An icon to use to visualize the variation. Either a string or object is accepted.
    *   **`attributes`:** An object that overrides the block’s attributes.
    *   **`innerBlocks`**: An array to handle the initial configuration of nested blocks.
    *   **`example`:** An object that provides structured data for the block preview. Can be set to `undefined` to disable the preview.
    *   **`scope`:** A list of scopes where the block can be used. Available options are: `block`, `inserter`, and `transform`.
    *   **`isDefault`:** Whether to set the variation as the default variation of the block. Defaults to `false`.
    *   **`isActive`:** A function or array of block attributes used to determine if the variation is active when the block is selected.
 -->

*   **`blockName`:** バリエーションを登録するための、(名前空間を含む) ブロックの名称です。
*   **`variation`:** バリエーションを構成するためのオプションのオブジェクトで、以下のプロパティのいずれかを含む場合があります:
    *   **`name`:** あなたのバリエーションの、一意なマシン可読スラッグです。
    *   **`title`:** あなたのバリエーションの、国際化可能な人間可読タイトルです。
    *   **`description`:** 追加された場合、バリエーションの、国際化可能な人間可読の説明です。
    *   **`category`:** 登録済みブロック・タイプ・カテゴリーのスラッグです
    *   **`keywords`:** 検索時にユーザーがバリエーションを発見するのに役立つ、キーワードの配列です。
    *   **`icon`:** バリエーションを可視化するための、アイコンです。文字列またはオブジェクトが使用可能です。
    *   **`attributes`:** ブロックの属性を上書きする、オブジェクトです。
    *   **`innerBlocks`**: ネストされたブロックの初期設定を、ハンドルするための配列です。
    *   **`example`:** ブロックのプレビュー用に構造化されたデータを提供するオブジェクトです。`undefined` に設定すると、プレビューを無効化できます。
    *   **`scope`:** ブロックが使用可能なスコープのリストです。利用可能なオプション: `block`、`inserter`、および `transform`。
    *   **`isDefault`:** ブロックのデフォルト・バリエーションとして、このバリエーションを設定するか否か。デフォルトは `false` です。
    *   **`isActive`:** ブロックが選択された際に、バリエーションが有効か否かを判断するための、ブロック属性の関数または配列です。

<!-- 
To learn more about block variations, read the [Block Variations API](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-variations/) documentation in the Block Editor Handbook.
 -->

ブロック・バリエーションについて詳しく知りたい場合は、ブロック・エディター・ハンドブックの [ブロック・バリエーション API](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-variations/) ドキュメントを御覧ください。

<!-- 
To build your custom variation, the most important thing is to think about the attributes that you want to control that will set this variation apart from the default block. That’s what makes a variation a *variation*.
 -->

あなたのカスタムバリエーションを構築する際、最も重要なのは、デフォルトのブロックと差別化するための、制御したい属性を考えることです。それが、バリエーションを*バリエーション* たらしめる所以です。

<!-- 
For Spacer block variations, this is likely to be the `height` attribute. Suppose you wanted it to have a default of `180px`. For your variation, you’d need to set `attributes.height` and also check if `180px` is the value of the attribute in the `isActive` callback function.
 -->

「スペーサー」ブロック・バリエーションの場合、これはおそらく `height` 属性です。仮にデフォルト値を `180px` にしたいとします。参考までに、`isActive` コールバック関数内の属性の値が `180px` の場合、`attributes.height` をセットし、確認する必要もあります。

<!-- 
Try this by pasting this code in your `block-variations.js` file:
 -->

このコードをあなたの `block-variations.js` ファイルにペーストして試してみてください:

```javascript
const { registerBlockVariation } = wp.blocks;
const { __ } = wp.i18n;

registerBlockVariation( 'core/spacer', {
	name:       'themeslug/spacer',
	title:      __( 'Theme Name: Spacer', 'themeslug' ),
	keywords:   [ 'space', 'spacer', 'spacing' ],
	attributes: {
		height: '180px'
	},
	isActive: ( blockAttributes ) =>
		blockAttributes.height && '180px' === blockAttributes.height
} );
```

<!-- 
Each block will have its own attributes, so you will need to dive into the block’s code to determine all of the available attributes you may want to overwrite for your variations. That is something beyond what can be covered in this doc, but the above code block should give you a solid starting point.
 -->

各ブロックには独自の属性があるため、ブロックのコードを詳細に確認し、あなたのバリエーションで上書きしたいすべての利用可能な属性を特定する必要があります。これはこのドキュメントでカバーできる範囲を超えた内容ですが、上記のコード・ブロックは、良い出発点となるはずです。

<!-- 
### Unregistering block variations
 -->

### ブロック・バリエーションの登録解除

<!-- 
To unregister a block variation, you must use the `unregisterBlockVariation()` JavaScript function. Here is a look at the function’s signature:
 -->

ブロック・バリエーションを登録解除するには、JavaScript `unregisterBlockVariation()` 関数を使用する必要があります。以下に、関数のシグネチャを示します:

```javascript
const unregisterBlockVariation = ( blockName, variationName )
```

<!-- 
The function accepts two parameters:
 -->

この関数は2つのパラメータを受け取ります:

<!-- 
*   **`blockName`:** The name of the block (including namespace) for the variation you want to unregister.
*   **`variationName`:** The name of the variation to unregister.
 -->

*   **`blockName`:** 登録解除したいバリエーションの、(名前空間を含む) ブロック名称です。
*   **`variationName`:** 登録解除するバリエーションの名称です。

<!-- 
Suppose that you wanted to remove the Spacer block variation that you just added from the previous section. All you need to do is plug in the block and variation names.
 -->

仮に、前のセクションで追加した「スペーサー」ブロック・バリエーションを削除したいとします。必要なのは、ブロック名とバリエーション名を指定するだけです。

<!-- 
Add this code at the end of your `block-variations.js` file to test it:
 -->

このコードをあなたの `block-variations.js` ファイルの末尾に追加して、テストしてください:

```javascript
wp.domReady( () => {
	wp.blocks.unregisterBlockVariation( 
		'core/spacer', 
		'themeslug/spacer' 
	);
} );
```

<!-- 
One important thing to note when unregistering variations is that you should wrap them in a `wp.domReady()` call. This is to ensure that the unregistering process happens later in the loading process after variations have already been registered.
 -->

バリエーションを登録解除する際の重要な点は、それらを `wp.domReady()` コールで囲む必要があることです。これは、バリエーションが登録された後に、登録解除プロセスがロードプロセスの後段で実行されるようにするためです。