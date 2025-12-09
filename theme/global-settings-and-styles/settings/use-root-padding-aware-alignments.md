<!-- 
# Use Root Padding Aware Alignments
 -->

# ルート・パディング対応配置の使用

<!-- 
The `settings.useRootPaddingAwareAlignments` property can be one of the most confusing settings in `theme.json`. It is not tied to an interface option. Nor is it used for registering presets. Instead, it’s for configuring where WordPress places your theme’s horizontal padding styles.
 -->

`settings.useRootPaddingAwareAlignments` プロパティは、`theme.json` の中で最も混乱を招きやすい設定の一つです。これはインターフェース・オプションに関連付けられていません。プリセットの登録にも使用されません。代わりに、WordPress が、あなたのテーマの水平方向のパディング・スタイルを、どこに配置するかを設定するためのものです。

<!-- 
This means it works in conjunction with `styles.spacing.padding` in `theme.json`. You can find out more about general styling in the [Styles documentation](https://developer.wordpress.org/themes/global-settings-and-styles/styles), but you’ll learn how this specific style works alongside this setting here.
 -->

これは、`theme.json` 内の `styles.spacing.padding` と連動して機能することを意味します。一般的なスタイル設定については [スタイル・ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/styles) で詳細をご覧いただけますが、この特定のスタイルが本設定とどのように連携するかは、ここで学んでいただけます。

<!-- 
## What is root padding?
 -->

## ルート・パディングって ?

<!-- 
Before understanding how the `settings.useRootPaddingAwareAlignments` property works, you must first understand what root padding is.
 -->

`settings.useRootPaddingAwareAlignments` プロパティの動作を理解する前に、まずルート・パディングとは何かを理解する必要があります。

<!-- 
Root padding is the padding that is applied to a web page’s “root” element. In the case of WordPress themes, this is the `<body>` element. To customize the spacing for the root element, you must target the `styles.spacing.padding` element in `theme.json`.
 -->

ルート・パディングとは、Web ページの「ルート」要素に適用されるパディングです。WordPress テーマの場合、これは `<body>` 要素です。ルート要素の余白をカスタマイズするには、`theme.json` 内の `styles.spacing.padding` 要素をターゲットにする必要があります。

<!-- 
Take the following `theme.json` snippet, for example. It adds `0` for top and bottom padding and `2rem` for left and right padding:
 -->

たとえば、次の `theme.json` スニペットを見てみましょう。これは、上と下のパディングに `0` を、左と右のパディングに `2rem` を追加します:

```json
{
	"version": 2,	
	"styles": {
		"spacing": {
			"padding": {
				"top": "0",
				"bottom": "0",
				"left": "2rem",
				"right": "2rem"
			}
		}
	}
}
```

<!-- 
By default, this will add `2rem` of padding on the left and right sides of the `<body>` (root) element.
 -->

デフォルトでは、これにより `<body>` (ルート) 要素の左右両側に `2rem` のパディングが追加されます。

<!-- 
As shown in this screenshot, there is horizontal padding at the root, and a full-width Cover block stretches until it hits that padding:
 -->

このスクリーンショットに示されているように、ルートに水平方向のパディングがあり、全幅の「カバー」ブロックは、そのパディングに到達するまで伸びています:

<!-- 
[![WordPress site header with a Cover block background. It has padding to the left and right of it so that it doesn't stretch the full width of the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding.jpg?resize=2048%2C1024&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding.jpg?ssl=1)
 -->

[![背景が「カバー」ブロックになっている、WordPress のサイトヘッダー。その左右にパディングが設定されていて、画面の全幅まで広がらないようになっている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding.jpg?resize=2048%2C1024&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding.jpg?ssl=1)

<!-- 
This is the CSS that WordPress outputs based on the above `theme.json` code:
 -->

これは上記の `theme.json` コードにもとづいて、WordPress が出力する CSS です:

```css
body {
	padding-top: 0;
	padding-right: 2rem;
	padding-bottom: 0;
	padding-left: 2rem;
}
```

<!-- 
But—and this is where things can look odd to seasoned designers—when `settings.useRootPaddingAwareAlignments` is enabled, the “root” padding is no longer applied to the root element. It is applied to container blocks like Group. 
 -->

しかし — ここで経験豊富なデザイナーには、奇妙に映るかもしれないが — `settings.useRootPaddingAwareAlignments` が有効化されると、「ルート」パディングは、もはやルート要素には適用されなくなります。代わりに、「グループ」のようなコンテナ・ブロックに適用されます。

<!-- 
You’ll learn more about why this happens in the next section. The main goal right now is to understand that root padding is traditionally applied to the `<body>` element, and that is what most theme authors would expect.
 -->

この現象が起きる理由については、次セクションで詳しく説明します。現時点での主な目的は、ルート・パディングが伝統的に `<body>` 要素に適用されるものであり、ほとんどのテーマ作成者がそれを想定している、ということを理解することです。

<!-- 
For root padding aware alignments, WordPress is only concerned with the horizontal (left and right) padding. So the vertical (top and bottom) padding is not relevant to this documentation.
 -->

ルート・パディング対応の配置については、WordPress は水平方向 (左右) のパディングのみを扱います。したがって、垂直方向 (上下) のパディングは、このドキュメントでは関係ありません。

<!-- 
## Enabling root padding aware alignments
 -->

## ルート・パディング対応配置の有効化

<!-- 
By default, WordPress will apply root padding to the `<body>` element. If this makes sense for your theme’s design, you don’t need to do anything else.
 -->

デフォルトでは、WordPress は ルート・パディングを `<body>` 要素に適用します。これがあなたのテーマのデザインに適している場合、他に何もする必要はありません。

<!-- 
*But what if you want to let full-width items stretch to the edges of the screen* ***and*** *have padding on the root element?* 
 -->

*しかし、全幅の要素を画面の端まで伸ばし* ***つつ*** *ルート要素にパディングを設定したい場合は ?*

<!-- 
When compared to the first screenshot, notice how the Cover block stretches to edges of the screen but there is padding still applied to the nested blocks here:
 -->

最初のスクリーンショットと比較すると、「カバー」ブロックが画面の端まで伸びているのに、ネストされたブロックには、まだパディングが適用されていることに注目してください:

<!-- 
[![WordPress site header with a Cover block background that stretches the full width of the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding-aware.jpg?resize=1024%2C510&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding-aware.jpg?ssl=1)
 -->

[![画面の全幅に伸びる「カバー」ブロック背景がある、WordPress サイトヘッダー。](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding-aware.jpg?resize=1024%2C510&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/root-padding-aware.jpg?ssl=1)

<!-- 
This is a common design pattern, and there are several ways to stretch elements beyond their containers in CSS. But WordPress has a standard approach that would work with any theme.
 -->

これは一般的なデザイン・パターンであり、CSS には要素をコンテナの外に伸ばす方法がいくつか存在します。しかし WordPress には、どのテーマでも機能する標準的な手法があります。

<!-- 
That’s where `settings.useRootPaddingAwareAlignments` comes in. When this property is set to `true`, it puts the root padding on container elements instead of `<body>`. This must also be combined with a `styles.spacing.padding` object, particularly with horizontal padding applied.
 -->

そこで `settings.useRootPaddingAwareAlignments` が役立ちます。このプロパティを `true` に設定すると、ルート・パディングが `<body>` ではなくコンテナ要素に適用されます。また、特に水平方向のパディングを適用する場合は、`styles.spacing.padding` オブジェクトとの併用が必須です。

<!-- 
Try this code in your `theme.json`:
 -->

このコードをあなたの `theme.json` で試してみましょう:

```json
{
	"version": 2,
	"settings": {
		"useRootPaddingAwareAlignments": true
	},	
	"styles": {
		"spacing": {
			"padding": {
				"top": "0",
				"bottom": "0",
				"left": "2rem",
				"right": "2rem"
			}
		}
	}
}
```

<!-- 
There is no right or wrong way to handle root padding. It is a situational setting where you must decide which option is best for your theme’s design.
 -->

ルート・パディングの処理方法には、正解も不正解もありません。これは状況に応じた設定であり、あなたのテーマのデザインに最適な選択肢を、判断する必要があります。

<!-- 
### How does this work?
 -->

### これは、どのように機能するの ?

<!-- 
It’s not particularly vital to know how WordPress handles all of this under the hood, but sometimes you might just want a deeper understanding of what’s going on.
 -->

WordPress が内部でこれらをどのように処理しているかを詳しく知る必要は必ずしもありませんが、時には何が起きているのかを深く理解したいと思うこともあるでしょう。

<!-- 
When you enable `settings.useRootPaddingAwareAlignments`, as shown in the last `theme.json` example, WordPress will generate two new bits of CSS. The first is that it defines some CSS custom properties for the root padding:
 -->

先ほどの `theme.json` の例で示したように、`settings.useRootPaddingAwareAlignments` を有効にすると、WordPress は 新しい CSS を2つ生成します。1つ目は、ルート・パディング用の CSS カスタム・プロパティを定義するものです:

```css
body {
	--wp--style--root--padding-top: 0;
	--wp--style--root--padding-right: 2rem;
	--wp--style--root--padding-bottom: 0;
	--wp--style--root--padding-left: 2rem;
}
```

<!-- 
The second is that it adds a `.has-global-padding` class:
 -->

2つ目は、`.has-global-padding` クラスを追加することです:

```css
.has-global-padding {
	padding-right: var(--wp--style--root--padding-right);
	padding-left: var(--wp--style--root--padding-left);
}
```

<!-- 
This class is then given to container blocks with constrained layouts (for example, Group blocks with the **Layout > Inner blocks use content width** option enabled):
 -->

それから、このクラスは制約付きレイアウトを持つコンテナ・ブロックに付与されます (たとえば、**レイアウト > コンテンツ幅を使用するインナー・ブロック** オプションが有効な「グループ」ブロック):

```markup
<div class="wp-block-group has-global-padding is-layout-constrained wp-block-group-is-layout-constrained">
	<!-- nested blocks... -->
</div>
```

<!-- 
Beyond that, WordPress adds inline CSS to stretch nested wide and full-width blocks beyond their parent block’s width (including the additional padding that’s added to the width).
 -->

さらに、WordPress は、ネストされたワイドブロックや全幅ブロックを、その親ブロックの幅 (その幅に追加されるパディングも含む) を超えて伸ばすために、インライン CSS を追加します。