<!-- 
# Applying Styles
 -->

# スタイルの適用

<!-- 
Traditionally, theme authors would style everything from a stylesheet—and they still sometimes must. In modern WordPress, you can also style most, if not all, of your theme directly from your `theme.json` file.
 -->

従来、テーマ作者はスタイルシートからすべてをスタイル設定していました — が、今でもそうしなければならない場合があります。最近の WordPress では、`theme.json` ファイルから直接、すべてではないにせよ、あなたのテーマの大部分をスタイル設定できます。

<!-- 
When you use this standard system, it is also reflected in the **Appearance > Editor > Styles** interface. This means your theme’s users with access to that admin screen can also make changes that easily work alongside your theme’s styles. But it also means that you can design your theme directly from this visual interface if you choose to do so.
 -->

この標準システムを使用すると、**外観 > エディター > スタイル** インターフェースにも反映されます。これは、その管理画面へのアクセス権を持つあなたのテーマのユーザーも、あなたのテーマのスタイルと容易に連携する変更を加えられることを意味します。しかし同時に、必要に応じてこのビジュアル・インターフェースから直接あなたのテーマをデザインできるという利点も意味します。

<!-- 
`theme.json` supports styles at three different levels:
 -->

`theme.json` は、3つの異なるレベルで、スタイルをサポートします:

<!-- 
*   Root (global)
*   Elements
*   Blocks
 -->

*   ルート (グローバル)
*   要素
*   ブロック

<!-- 
In this document, you will learn the syntax necessary for styling each of these things via JSON.
 -->

本ドキュメントでは、JSON を介してこれらのそれぞれに対してスタイル設定するために必要な構文について学びます。

<!-- 
## Styling the root element
 -->

## ルート要素のスタイル設定

<!-- 
When referring to the “root” element in WordPress themes, we’re specifically talking about the HTML `<body>` tag. It’s the root of the visual output for the page.
 -->

WordPress テーマにおける「ルート」要素とは、具体的には HTML の `<body>` タグを指します。これはページの視覚的出力の根幹となる要素です。

<!-- 
Technically, when styling the root element, you are adding *global* styles that trickle down through the design and are used unless a more specific element or block style overrides them. For example, you’ll likely want to set a default font-family or font-size that is used across the entire design. But you’ll, of course, want to change that in specific instances.
 -->

技術的に言えば、ルート要素にスタイル設定する際、より具体的な要素やブロック・スタイルで上書きされない限り、デザイン全体に浸透する *グローバル* スタイルを追加していることになります。たとえば、デザイン全体で使用されるデフォルトのフォント・ファミリーやフォント・サイズを設定したいでしょう。そして、特定のケースでは、当然ながらそれを変更したいはずです。

<!-- 
Because these are global styles, it means that they belong directly under the `styles` property.
 -->

これらはグローバル・スタイルであるため、`styles` プロパティ下に属します。

<!-- 
So let’s add a default text and background color to show how this works:
 -->

それでは、デフォルトのテキストと背景色を追加して、これがどのように機能するかを確認しましょう:

```json
{
	"version": 2,
	"styles": {
		"color": {
			"text": "#000000",
			"background": "#f5f1ea"
		}
	}
}
```

<!-- 
As you can see, the `color` property is nested directly beneath the `styles` property. This means that the `text` and `background` colors are applied directly to the `<body>` element by WordPress, resulting in this CSS in the editor and on the front end:
 -->

ご覧の通り、`color` プロパティは `styles` プロパティ下にネストされています。これは、`text` と `background` の色が WordPress によって `<body>` 要素に直接適用されることを意味し、その結果、エディター上およびフロントエンドでは、以下の CSS が適用されます:

```css
body {
	background: #f5f1ea;
	color: #000000;
}
```

<!-- 
And because of the way the *cascade* works in CSS, these colors will be used for everything, unless a more specific style rule overwrites it.
 -->

CSS における *カスケード* のしくみ上、より具体的なスタイルルールで上書きされない限り、これらの色はあらゆる要素に適用されます。

<!-- 
If you open your site on the front end or via **Appearance > Editor** in the WordPress admin, you should see your colors applied:
 -->

フロントエンドであなたのサイトを開くか、WordPress 管理画面の **外観 > エディター** から開くと、あなたのカラーが適用されているのが確認できるはずです:

<!-- 
[![WordPress Site Editor with Styles interface open, showing the theme's colors.](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-root-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-root-colors.jpg?ssl=1)
 -->

[![テーマの色が反映された、スタイル・インターフェースを開いた WordPress サイトエディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-root-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-root-colors.jpg?ssl=1)

<!-- 
You are not just limited to colors. You can add `typography`, `spacing`, and more here. The root element supports almost all of the available style properties, which you can reference in the [Supported Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) documentation.
 -->

色だけに限定されるわけではありません。ここでは `typography` や `spacing` などを追加できます。ルート要素は利用可能なスタイル・プロパティのほぼすべてをサポートしており、[サポートされているスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) ドキュメントで参照できます。

<!-- 
The `styles.spacing.padding` property has a unique use case when used in conjunction with `settings.useRootPaddingAwareAlignments`. For more information on how these two work together, read the [Use Root Padding Aware Alignments](https://developer.wordpress.org/themes/global-settings-and-styles/use-root-padding-aware-alignments/) documentation.
 -->

`styles.spacing.padding` プロパティは、`settings.useRootPaddingAwareAlignments` と組み合わせて使用する場合に、特有のユースケースがあります。これら2つの連携に関する詳細は、[ルート・パディング対応アライメントの使用](https://developer.wordpress.org/themes/global-settings-and-styles/use-root-padding-aware-alignments/) ドキュメントをご覧ください。

<!-- 
## Styling elements
 -->

## 要素のスタイル設定

<!-- 
WordPress has a standard system for styling elements via `theme.json`. In this case, “elements” usually maps to actual HTML elements. But there are cases where it’s referring to something that doesn’t map directly to a single HTML element. In general, these should be reasonably straightforward.
 -->

WordPress には、`theme.json` を介した要素のスタイル設定のための標準システムがあります。この場合、「要素」は通常、実際の HTML 要素に対応します。ただし、個別の HTML 要素に直接対応しないものを指す場合もあります。一般的に、これらは比較的単純であるべきです。

<!-- 
Just like styling the root element and blocks, which you’ll learn about below, you can apply a wide range of the [supported styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) to elements.
 -->

ルート要素やブロックのスタイル設定と同様に (これについては後述します)、要素には [サポートされているスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) の幅広い範囲を適用できます。

<!-- 
The currently-supported elements are:
 -->

現在サポートされている要素は、以下の通りです:

<!-- 
*   **`button`:** Applied to `<button>` elements and button-like links, such as that used for the Button block.
*   **`caption`:** Applied to media captions, which are wrapped in a `<figcaption>` element.
*   **`cite`:** Applied to the `<cite>` element when used for citations, such as that used for the Quote and Pullquote blocks.
*   **`heading`:** Applied to all heading elements from `<h1>` through `<h6>`, but these can be overridden for individual headings.
*   **`h1 - h6`:** Each of the `<h1>` through `<h6>` elements can be individually styled.
*   **`link`:** Applied to the `<a>` tag, which is used to create links.
 -->

*   **`button`:** 「ボタン」ブロックで使用されるような、`<button>` 要素およびボタン風のリンクに適用されます。
*   **`caption`:** `<figcaption>` 要素で囲まれた、メディア・キャプションに適用されます。
*   **`cite`:** 引用に使用される場合、「引用」ブロックや「プルクオート」ブロックで使用されるような、`<cite>` 要素に適用されます。
*   **`heading`:** `<h1>` から `<h6>` までのすべての見出し要素に適用されますが、個々の見出しに対して上書きできます。
*   **`h1 - h6`:** `<h1>` から `<h6>` までの各要素は、個別にスタイル設定できます。
*   **`link`:** リンクを作成するために使用される `<a>` タグに適用されます。

<!-- 
Let’s try a real example now. Suppose you wanted to give all buttons across the site a white text color that sits atop a red background. You need to target the `text` and `background` properties of `styles.elements.button.color`.
 -->

実際の例を見てみましょう。サイト全体のボタンに、赤い背景の上に、白い文字色を設定したいとしましょう。`styles.elements.button.color` の `text` プロパティと `background` プロパティを対象とする必要があります。

<!-- 
Add this code to your `theme.json` file:
 -->

あなたの `theme.json` ファイルに、このコードを追加してください:

```json
{
	"version": 2,
	"styles": {
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#aa3f33"
				}
			}
		}
	}
}
```

<!-- 
If you view a button in the Site Editor or on the front end of the site, you should see these colors applied:
 -->

サイトエディターまたはサイトのフロントエンドでボタンを表示すると、これらの色が適用されているはずです:

<!-- 
[![WordPress Style Book with the Buttons block highlighted and the Text color option expanded.](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-elements-button.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-elements-button.jpg?ssl=1)
 -->

[![「ボタン」ブロックが強調表示され、テキストカラー・オプションが展開された、WordPress スタイルブック。](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-elements-button.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-elements-button.jpg?ssl=1)

<!-- 
Some elements both serve as element styles and the foundation of more specific blocks. In the case of elements that also tie into blocks, the block styles will overrule the element styles. For example, the Button and Heading blocks can have their own styles but they will fall back to the `button` and `heading` element styles.
 -->

一部の要素は、要素スタイルとして機能すると同時に、より具体的なブロックの基盤にもなります。ブロックにも関連する要素の場合、ブロック・スタイルが要素スタイルに優先します。たとえば、「ボタン」ブロックや「見出し」ブロックは独自のスタイルを持つことができますが、これらは `button` 要素スタイルや `heading` 要素スタイルにもフォールバックします。

<!-- 
WordPress will generate this CSS in both the editor and on the front end for your `button` element styles:
 -->

WordPress は、あなたの `button` 要素のスタイルに対して、エディターとフロントエンドの両方でこの CSS を生成します:

```css
.wp-element-button, 
.wp-block-button__link {
	background-color: #aa3f33;
	color: #ffffff;
}
```

<!-- 
WordPress sometimes—but not always—gives elements a specific CSS class with the naming scheme of `.wp-element-{$element}`. For example, button elements have the `.wp-element-button` class. The styles you provide via `theme.json` are then applied to that CSS class.
 -->

WordPress は、— 常にではないが — 要素に対して `.wp-element-{$element}` という命名規則の、特定の CSS クラスを付与することがあります。たとえば、ボタン要素には `.wp-element-button` クラスが付与されます。`theme.json` 経由で提供したスタイルは、この CSS クラスに適用されます。

<!-- 
As you can see in the generated CSS, WordPress is targeting the `.wp-element-button` class when styling the `button` element. But it’s also specifically targeting the `.wp-block-button__link` class for backward compatibility with the Button block.
 -->

生成された CSS でわかるように、WordPress は `button` 要素のスタイル設定において `.wp-element-button` クラスを対象としています。ただし、「ボタン」ブロックとの下位互換性を確保するため、特に `.wp-block-button__link` クラスも対象としています。

<!-- 
### Styling pseudo-classes
 -->

### 疑似クラスのスタイル設定

<!-- 
You can also add style properties for a standard set of CSS pseudo-classes for some elements. Generally, this will be for features like link hover and focus styles.
 -->

一部の要素に対して、標準的な CSS 疑似クラスのスタイル・プロパティも追加できます。一般的に、これはリンクのホバーやフォーカス時のスタイルといった機能向けになります。

<!-- 
The `button` and `link` elements support these pseudo-classes:
 -->

`button` 要素と `link` 要素は、以下の疑似クラスをサポートします:

*   `:hover`
*   `:focus`
*   `:active`
*   `:visited`

<!-- 
Each pseudo-class must be added as a property nested under the element you want to style. For example, you must target `styles.elements.link.:hover` to customize link hover styles.
 -->

各疑似クラスは、スタイルを適用したい要素下にネストされたプロパティとして、追加する必要があります。たとえば、リンクのホバースタイルをカスタマイズするには、`styles.elements.link.:hover` を対象とする必要があります。

<!-- 
Let’s look at this in context using the previous example of styling `button` elements. Suppose you wanted to change the background color when a user’s mouse hovers over buttons. Use this `theme.json` code to achieve that:
 -->

この文脈で、`button` 要素のスタイル設定という、前の例を使って見てみましょう。ユーザーがボタンにマウスをホバーした際に、背景色を変更したいとしましょう。これを実現するには、以下の `theme.json` コードを使用します:

```json
{
	"version": 2,
	"styles": {
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#aa3f33"
				},
				":hover": {
					"color": {
						"background": "#822f27"
					}
				}
			}
		}
	}
}
```

<!-- 
## Styling blocks
 -->

## ブロックのスタイル設定

<!-- 
One of the great things about the block system is that it provides a standardized system for styling any block. This means that you can add styles for core WordPress blocks as well as third-party plugin blocks directly in `theme.json`.
 -->

ブロック・システムの優れた点の一つは、あらゆるブロックのスタイル設定を標準化するしくみを提供していることです。つまり、WordPress のコアブロックだけでなくサードパーティ製プラグインのブロックに対しても、`theme.json` 内で直接スタイルを追加できます。

<!-- 
To style a specific block, you must target `styles.blocks.blockname` in your `theme.json` file. From there, you can add any of the block’s [supported styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/).
 -->

特定のブロックをスタイル設定するには、あなたの `theme.json` ファイル内で `styles.blocks.blockname` を対象とする必要があります。そこから、そのブロックの [サポートされているスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) を追加できます。

<!-- 
Let’s take a look at a basic example. Assume that you want to give a slightly rounded border to all Image blocks. For this, you need to target the `border.radius` property.
 -->

基本的な例を見てみましょう。すべての「画像」ブロックに、微妙な角丸の枠線を与えたいとしましょう。その為には、`border.radius` プロパティを対象とする必要があります。

<!-- 
Add this code to your `theme.json` file:
 -->

あなたの `theme.json` ファイルに、このコードを追加してください:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/image": {
				"border": {
					"radius": "6px"
				}
			}
		}
	}
}
```

<!-- 
This should make any instance of the Image block on your site appear with a rounded border:
 -->

これにより、あなたのサイト上の「画像」ブロックのインスタンスは、すべて角丸の枠線で表示されるはずです:

<!-- 
[![WordPress Style book with the Image block highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-blocks-image.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-blocks-image.jpg?ssl=1)
 -->

[![「画像」ブロックが強調表示された、WordPress スタイルブック。](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-blocks-image.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-blocks-image.jpg?ssl=1)

<!-- 
WordPress will also generate this CSS for the nested `<img>` element within the Image block for both the editor and front end:
 -->

WordPress は、エディターとフロントエンドの両方において、「画像」ブロック内のネストされた `<img>` 要素に対してこの CSS も生成します:

```css
.wp-block-image img {
	border-radius: 6px;
}
```

<!-- 
You can add styles for as many or as few blocks as you want. That’s entirely up to you and what you want to accomplish with your design. Have fun with it!
 -->

ブロックの数に関係なく、好きなだけスタイルを追加できます。それは完全にあなた次第であり、あなたのデザインで何を達成したいかによります。楽しんでください !

<!-- 
For a full list of core WordPress blocks that you can style, visit the [Core Blocks Reference](https://developer.wordpress.org/block-editor/reference-guides/core-blocks/). Note that this does not include blocks from plugins and other third-party sources.
 -->

スタイル設定可能な WordPress のコアブロックの完全な一覧については、[コアブロック・リファレンス](https://developer.wordpress.org/block-editor/reference-guides/core-blocks/) をご覧ください。なお、プラグインやその他のサードパーティ・ソースからのブロックは含まれていません。

<!-- 
When targeting a block’s styles, you must know both its namespace and slug. Above, you learned that the Image block has the namespace (`core`) and slug (`image`), creating the namespace/slug combination of `core/image`. All core WordPress blocks have the `core` namespace, and you can find this information for any block (including from third-party plugins) in its `block.json` file.
 -->

ブロックのスタイルを対象とする際には、その名前空間とスラッグの両方を把握する必要があります。上記で学んだように、「画像」ブロックは名前空間 (`core`) とスラッグ (`image`) を持ち、これらが組み合わさって `core/image` という名前空間/スラッグの組み合わせを形成します。すべての WordPress のコアブロックは `core` 名前空間を持ち、(サードパーティ製プラグインを含む) 任意のブロックに関するこの情報は、その `block.json` ファイルで確認できます。

<!-- 
### Styling elements nested in blocks
 -->

### ブロック内にネストされた要素のスタイル設定

<!-- 
You can also add custom styles for elements that are nested within blocks. This feature gives you a lot of flexibility for contextually styling elements directly within `theme.json`.
 -->

ブロック内のネストされた要素に対して、カスタム・スタイルも追加できます。この機能により、`theme.json` 内で文脈に即した要素のスタイル設定を、柔軟に行えます。

<!-- 
When styling a block’s nested elements, you must pass an `elements` object directly under the block property: `styles.blocks.blockname.elements`.
 -->

ブロックのネストされた要素にスタイル設定する際は、ブロックプロパティ下に `elements` オブジェクトを渡す必要があります: `styles.blocks.blockname.elements`。

<!-- 
Suppose you wanted a large font size for the PullQuote block but you wanted to create a fluid size for its nested `<cite>` element that never grew larger than `50%` of the parent block or `1.5rem`, whichever is the larger of the two.
 -->

「プルクオート」ブロックには大きなフォントサイズを設定したいが、その中にネストされた `<cite>` 要素には、親ブロックの50%または `1.5rem` のいずれか大きいほうを超えないよう、可変サイズを設定したい場合を想定しましょう。

<!-- 
For this, you need to define the `typography.fontSize` for both the `core/pullquote` block and its nested `cite` element in `theme.json`:
 -->

これを行うには、`theme.json` 内で `core/pullquote` ブロックとそのネストされた `cite` 要素の両方に対して、`typography.fontSize` を定義する必要があります:

```json
{
	"version": 2,
	"styles": {
		"elements": {
			"core/pullquote": {
				"typography": {
					"fontSize": "2.25rem"
				},
				"elements": {
					"cite": {
						"typography": {
							"fontSize": "max( 50%, 1.5rem )"
						}
					}
				}
			}
		}
	}
}
```

<!-- 
The font-size will now look like this in the editor:
 -->

フォントサイズはエディター上で、以下のように表示されます:

<!-- 
[![WordPress post editor with a Pullquote block and nested cite element.](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-element-cite.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-element-cite.jpg?ssl=1)
 -->

[![「プルクオート」ブロックと、ネストされた cite 要素がある、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-element-cite.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-element-cite.jpg?ssl=1)

<!-- 
WordPress generates this CSS for styling both the Pullquote block and its nested `<cite>` element:
 -->

WordPress は、「プルクオート」ブロックと、その中にネストされた `<cite>` 要素の両方のスタイル設定のために、この CSS を生成します:

```css
.wp-block-pullquote {
	font-size: 2.25rem;
}

.wp-block-pullquote cite {
	font-size: max( 50%, 1.5rem );
}
```

<!-- 
### Styling block style variations (block styles)
 -->

### ブロック・スタイル・バリエーションのスタイル設定 (ブロック・スタイル)

<!-- 
Since WordPress 6.2, you can customize the core block style variations (i.e., block styles) via `theme.json`. This feature allows you to use [supported styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) without having to write custom CSS in a separate stylesheet.
 -->

WordPress 6.2以降、`theme.json` を通じてコアブロックのスタイル・バリエーション (つまりブロック・スタイル) をカスタマイズできます。この機能により、別途スタイルシートにカスタム CSS を記述しなくても [サポートされているスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/) を利用できます。

<!-- 
To customize a block style variation, you must add a nested `variations` property within the block you want to style in `theme.json`. Then, each variation can use any of the block’s supported styles.
 -->

ブロックのスタイル・バリエーションをカスタマイズするには、`theme.json` でスタイルを設定したいブロック内にネストされた `variations` プロパティを追加する必要があります。その後、各バリエーションは、ブロックがサポートする任意のスタイルを使用できます。

<!-- 
Let’s walk through an example of modifying the Button block’s Outline style variation. Suppose you wanted to define the border color, style, and width that is specific to this block style variation.
 -->

「ボタン」ブロックの「アウトライン」スタイル・バリエーションを修正する例を見ていきましょう。このブロックのスタイル・バリエーションに、固有の枠線の色、スタイル、幅を定義したいとしましょう。

<!-- 
Add this code to your `theme.json`:
 -->

あなたの `theme.json` に、このコードを追加してください:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/button": {
				"variations": {
					"outline": {
						"border": {
							"color": "currentColor",
							"style": "solid",
							"width": "2px"
						}
					}
				}
			}
		}
	}
}
```

<!-- 
You should now see these changes reflected in the editor when the Outline block style variation is selected for the Button block:
 -->

「ボタン」ブロックで「アウトライン」ブロック・スタイル・バリエーションを選択すると、エディターにこれらの変更が反映されるはずです:

<!-- 
[![WordPress post editor with four Button blocks in a 2x2 grid. Two of the buttons have a filled background, and the other two are outlined.](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-variations-button.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-variations-button.jpg?ssl=1)
 -->

[![2×2グリッドに配置された、4つの「ボタン」ブロックが並ぶ、WordPress 投稿エディター。ボタン2つは塗りつぶし背景、残り2つは枠線のみ。](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-variations-button.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/styles-block-variations-button.jpg?ssl=1)

<!-- 
The currently available blocks and their core WordPress style variations are:
 -->

現在利用できるブロックと、その WordPress のコアスタイル・バリエーションは、以下の通りです:

*   **`core/button`:** `outline`, `fill`
*   **`core/image`:** `rounded`
*   **`core/quote`:** `plain`
*   **`core/site-logo`:** `rounded`
*   **`core/separator`:** `wide`, `dots`
*   **`core/social-links`:** `logos-only`, `pill-shape`
*   **`core/table`:** `stripes`
*   **`core/tag-cloud`:** `outline`

<!-- 
For a deeper dive into customizing block style variations, check out [Customizing core block style variations via theme.json](https://developer.wordpress.org/news/2023/05/customizing-core-block-style-variations-via-theme-json/) on the WordPress Developer Blog.
 -->

ブロックのスタイル・バリエーションをカスタマイズする方法について、詳しく知りたい場合は、WordPress 開発者ブログの [theme.json 経由でコアブロックのスタイル・バリエーションのカスタマイズ](https://developer.wordpress.org/news/2023/05/customizing-core-block-style-variations-via-theme-json/) をご覧ください。

<!-- 
*Custom* block style variations are not currently supported in `theme.json`. There is an [open ticket for the feature](https://github.com/WordPress/gutenberg/issues/49602). For now, you are limited to the core block style variations.
 -->

ブロックのスタイル・バリエーションの *カスタマイズ* は、現時点では `theme.json` でサポートされていません。[機能に関するチケットが発行されています](https://github.com/WordPress/gutenberg/issues/49602)。現時点では、コアブロックのスタイル・バリエーションに制限されます。