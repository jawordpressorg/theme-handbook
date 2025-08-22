<!-- 
# Block Stylesheets
 -->

# ブロック・スタイルシート

<!-- 
When styling blocks, you should always do so via the [`theme.json` styles property](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) if possible. This ensures that your styles have the best compatibility across the system, working alongside the default WordPress styles, those added by plugins, and user customizations.
 -->

ブロックをスタイル設定する際は、可能な限り [`theme.json` スタイル・プロパティ](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) を使用してください。これにより、デフォルトの WordPress スタイル、プラグインによって追加されたスタイル、およびユーザーによるカスタマイズと連動して、システム全体であなたのスタイルの互換性が最大限に確保されます。

<!-- 
But there are times when you simply need to step outside of what’s easily achievable via `theme.json`. For those cases, you should use WordPress’ built-in block stylesheets system.
 -->

しかし、`theme.json` 経由で簡単に実現できる以上のことを、どうしても必要とする場合もあります。そのような場合は、WordPress 内蔵のブロック・スタイルシート・システムを使用すべきです。

<!-- 
In this article, you will learn how to register per-block stylesheets, but remember that `theme.json` should be your first choice for styling in most cases.
 -->

本稿では、ブロック単位でのスタイルシートの登録方法について説明しますが、ほとんどのケースではスタイリングに `theme.json` を優先して選択すべきです。

<!-- 
## Why use block stylesheets?
 -->

## ブロック・スタイルシートを使う理由って ?

<!-- 
The primary use case for block stylesheets is when you have too much CSS to add to [`styles.blocks.{blockname}.css`](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/#css) in `theme.json`. This property allows you to add custom CSS, but it’s only ideal when it’s just a small bit of code. This is because you lose out on syntax highlighting and must place everything in a single line (JSON doesn’t support line breaks).
 -->

ブロック・スタイルシートの主なユースケースとは、`theme.json` に [`styles.blocks.{blockname}.css`](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/#css) に追加する CSSS があまりにも多い場合です。コードがごく短い場合、このプロパティを使用するとカスタム CSS を追加できるが、これは理想的な方法ではありません。これは、構文ハイライトが利用できず、すべてを1行に配置する必要があるためです (JSON は改行をサポートしていない)。

<!-- 
You may also be tempted to put all your custom CSS into your theme’s primary `style.css` file. That may be OK for some use cases, but the block stylesheets system often offers better performance by only loading the block’s CSS if the block is in use on a page. On the front end, it will also inline this code within the `<head>` area.
 -->

あなたのテーマの主要な `style.css` ファイルに、あなたのカスタム CSS をすべて配置したくなるかもしれません。一部のユースケースでは問題ないかもしれませんが、the ブロック・スタイルシート・システムは、ページで使用されているブロックの CSS のみをロードすることで、通常より優れたパフォーマンスを提供します。フロントエンドでは、このコードを `<head>` エリア内にインラインで埋め込みます。

<!-- 
Creating separate stylesheets for individual blocks is also beneficial for larger and more complex projects that have a lot of custom CSS for many different blocks. The separation of the files makes it easier to organize and manage your code.
 -->

個々のブロックごとに個別のスタイルシートを作成することは、さまざまなブロックに多くのカスタム CSS がある、大規模で複雑なプロジェクトにも有益です。ファイルを分離することで、あなたのコードの編成と管理が容易になります。

<!-- 
## Creating block stylesheets
 -->

## ブロック・スタイルシートの制作

<!-- 
To create custom block stylesheets, there are three steps you must take:
 -->

カスタム・ブロック・スタイルシートを制作するには、以下の3つの手順が必要です:

<!-- 
1.  Decide on an organizational and naming scheme.
2.  Write your custom CSS.
3.  Register your custom block stylesheet(s).
 -->

1.  構造と命名規則の決定。
2.  あなたのカスタム CSS の記述。
3.  あなたのカスタム・ブロック・スタイルシートの登録。

<!-- 
### Organizing and naming block stylesheets
 -->

### ブロック・スタイルシートの構成と命名

<!-- 
Before registering a block stylesheet, you first need to know what folder you will store your custom block stylesheets in. This can be anywhere you choose (there is no standard location), and the code below will assume you are putting block stylesheets in an `/assets/blocks` folder in your theme.
 -->

ブロック・スタイルシートを登録する前に、まず、あなたのカスタム・ブロック・スタイルシートを保存するフォルダーを決定する必要があります。これは任意の場所を選択できます (標準の場所は存在しない) し、以下のコードは、あなたのテーマ内の `/assets/blocks` フォルダーにブロック・スタイルシートを配置することを前提としています。

<!-- 
You should also decide on how you will name your CSS files. Again, there is no standard naming convention, but a good option is to use the block namespace and slug like so: `{namespace}-{slug}.css`. With this naming convention, a stylesheet for the `core/group` block would become `core-group.css`.
 -->

あなたの CSS ファイルの命名方法も決定する必要があります。また、標準的な命名規則はありませんが、良い選択肢として、ブロックの名前空間とスラッグを次のように使用します: `{namespace}-{slug}.css`。この命名規則に従うと、`core/group` ブロック用のスタイルシートは `core-group.css` になります。

<!-- 
Here is an example structure of what this could look like with CSS files for a few core blocks:
 -->

以下は、いくつかのコア・ブロック用の CSS ファイルを使用した際の、構造の例です:

*   `assets/`
    *   `blocks/`
        *   `core-group.css`
        *   `core-image.css`
        *   `core-media-text.css`

<!-- 
### Adding CSS to a block stylesheet
 -->

### ブロック・スタイルシートへの CSS の追加

<!-- 
To style a core block, the most important thing you need to know is its CSS class. This is automatically generated according to the block’s namespace and slug in the form of `.wp-block-{namespace}-{slug}`.
 -->

コア・ブロックをスタイル設定する際、最も重要なのはその CSS クラスです。これは、ブロックの名前空間とスラッグにもとづいて自動的に生成され、形式は `.wp-block-{namespace}-{slug}` になります。

<!-- 
Here is an example of styling a block with the namespace and slug of `super/duper` would look like:
 -->

以下は、名前空間とスラッグが `super/duper` のブロックをスタイリングした例です:

```css
.wp-block-super-duper {
	/* custom CSS goes here. */
}
```

<!-- 
Core WordPress blocks are an exception to this naming rule. Their namespace is `core`, but this is not included in any of the core blocks’ CSS classes. Instead, they use the `.wp-block-{slug}` format.
 -->

コア WordPress ブロックは、この命名規則の例外です。その名前空間は `core` ですが、これはコア・ブロックのどの CSS クラスにも含まれていません。その代わりに、`.wp-block-{slug}` フォーマットが使用されています。

<!-- 
It’s possible for third-party block developers to change the CSS class that gets output, so this general guide may not always be true for third-party blocks. In those cases, you will want to locate the block’s CSS class in the source code.
 -->

サードパーティのブロック開発者は、出力される CSS クラスを変更する可能性があり、そのため、この一般的なガイドは、サードパーティのブロックには必ずしも適用されない場合があります。そのような場合、ブロックの CSS クラスをソースコード内で特定する必要があります。

<!-- 
Suppose that you wanted to add some custom styling for the core Image block, which has the namespace and slug of `core/image`. You would need to target the `.wp-block-image` class.
 -->

名前空間とスラッグが `core/image` である、コア「画像」ブロックにカスタム・スタイルを追加したいとします。`.wp-block-image` クラスをターゲットにする必要があります。

<!-- 
Let’s try creating a gradient background, which essentially acts as a *faux* border for the `<img>` element within the Image block. The goal is to create a style that looks like this:
 -->

`<img>` 要素を「画像」ブロック内に配置し、その要素に *疑似* 枠線として機能するグラデーション背景を制作してみましょう。目標は、次のようなスタイルを制作することです:

<!-- 
[![WordPress post editor showing an image of palm trees with an orange-to-red gradient border.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-stylesheets-image-bg.jpg?resize=2048%2C923&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-stylesheets-image-bg.jpg?ssl=1)
 -->

[![オレンジから赤へのグラデーションの枠線で囲まれた、ヤシの木の画像を表示する WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-stylesheets-image-bg.jpg?resize=2048%2C923&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-stylesheets-image-bg.jpg?ssl=1)

<!-- 
First, create an `/assets/blocks/core-image.css` file in your theme. Then, add this CSS code to it:
 -->

まず、あなたのテーマ内に `/assets/blocks/core-image.css` ファイルを作成します。次に、この CSS コードをそのファイルに追加します:

```css
.wp-block-image img {
	padding: 1rem;
	background: linear-gradient(-60deg,#ff5858,#f09819);
}
```

<!-- 
Because this stylesheet isn’t registered, your custom styles won’t show in the editor or on the front end yet.
 -->

このスタイルシートが登録されていないため、あなたのカスタム・スタイルは、エディターやフロントエンドにまだ表示されません。

<!-- 
### Registering a block stylesheet
 -->

### ブロック・スタイルシートの登録

<!-- 
To register your block stylesheet, you will use the [`wp_enqueue_block_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) function. When registering block stylesheets, you should also execute the code on the `init` hook.
 -->

あなたの ブロック・スタイルシートを登録するには、[`wp_enqueue_block_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) 関数を使用します。ブロック・スタイルシートを登録する際は、`init` フックでコードを実行する必要があります。

<!-- 
The `wp_enqueue_block_style()` function accepts two parameters:
 -->

`wp_enqueue_block_style()` 関数は、2つのパラメータを受け付けます:

<!-- 
*   **`$block_name`:** The block name, including both the namespace and slug (e.g., `core/image`).
*   **`$args`:** An array of arguments that is passed to [`wp_register_style()`](https://developer.wordpress.org/reference/functions/wp_register_style/):
    *   **`handle`:** A unique handle for your stylesheet.
    *   **`src`:** The source URL for the stylesheet.
    *   **`path`:** The directory path for the stylesheet (needed to inline the CSS in `<head>`).
    *   **`deps`:** An array of registered stylesheet handles this stylesheet depends on.
    *   **`ver`:** A custom stylesheet version number.
    *   **`media`**: The media for which the stylesheet has been defined.
 -->

*   **`$block_name`:** 名前空間とスラッグを含む、ブロック名です (例: `core/image`)。
*   **`$args`:** [`wp_register_style()`](https://developer.wordpress.org/reference/functions/wp_register_style/) に渡される、引数の配列です:
    *   **`handle`:** あなたのスタイルシートの、一意なハンドルです。
    *   **`src`:** スタイルシート用の、ソース URL です。
    *   **`path`:** スタイルシート用の、ディレクトリ・パスです (`<head>` 内で CSS をインライン化するために必要)。
    *   **`deps`:** このスタイルシートが依存する、登録済みスタイルシートのハンドルの配列。
    *   **`ver`:** カスタム・スタイルシートのバージョン番号です。
    *   **`media`**: スタイルシートが定義されたメディアです。

<!-- 
To register your custom stylesheet for the Image block, add this code to your `functions.php` file:
 -->

「画像」ブロック用のあなたのカスタム・スタイルシートを登録するには、このコードをあなたの `functions.php` ファイルに追加してください:

```php
add_action( 'init', 'themeslug_enqueue_block_styles' );

function themeslug_enqueue_block_styles() {
	wp_enqueue_block_style( 'core/image', array(
		'handle' => 'themeslug-block-image',
		'src'    => get_theme_file_uri( "assets/blocks/core-image.css" ),
		'path'   => get_theme_file_path( "assets/blocks/core-image.css" )
	) );
}
```

<!-- 
You can also configure additional arguments for your call to `wp_enqueue_block_style()`, but the above is the minimum needed for WordPress to inline your CSS code in the `<head>` area of the site.
 -->

`wp_enqueue_block_style()` へのあなたのコールに、追加の引数も設定できるが、上記は、WordPress がサイトの `<head>` エリアにあなたの CSS コードをインラインで挿入するために必要な、最低限のものです。

<!-- 
For a deeper dive into block stylesheets, check out [Leveraging theme.json and per-block styles for more performant themes](https://developer.wordpress.org/news/2022/12/leveraging-theme-json-and-per-block-styles-for-more-performant-themes/) on the WordPress Developer Blog.
 -->

ブロック・スタイルシートについて詳しく知りたい人は、WordPress 開発者ブログの [`theme.json` とブロックごとのスタイルを活用し、より高性能なテーマを実現](https://developer.wordpress.org/news/2022/12/leveraging-theme-json-and-per-block-styles-for-more-performant-themes/) をご覧ください。