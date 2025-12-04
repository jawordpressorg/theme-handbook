<!-- 
# Typography
 -->

# タイポグラフィ

<!-- 
Typography is a wide-ranging subject in web design, and no single piece of documentation could do it justice. There are book-length works that dive into the finer details and articles aplenty across the web that teach best practices, tips, and tricks at length.
 -->

タイポグラフィは、Web デザインにおいて広範な主題であり、単一の文書ではそのすべてを網羅できません。詳細な部分まで掘り下げた書籍レベルの著作もあれば、ベストプラクティスやコツ、テクニックを長文で解説する記事も Web 上に数多く存在します。

<!-- 
This guide will specifically get you up to speed with the available settings available via `settings.typography` in `theme.json`.
 -->

本ガイドでは、`theme.json` 内の `settings.typography` 経由で利用可能な設定について、特に詳しく解説します。

<!-- 
Typography is also tightly related to spacing in your theme, so you will need to familiarize yourself with the [spacing settings](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing) to get the most out of both guides. You will also take what you learn from this documentation and apply it to your [`theme.json` styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles).
 -->

タイポグラフィはあなたのテーマにおける間隔設定とも密接に関連しているため、両方のガイドを最大限に活用するには [間隔の設定](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing) に慣れる必要があります。また、このドキュメントで学んだ内容をあなたの [`theme.json` スタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles) に適用することになります。

<!-- 
## Enabling and disabling typography options
 -->

## タイポグラフィ・オプションの有効化と無効化

<!-- 
There are several settings that are merely for enabling or disabling elements in the user interface. Each of these properties accept a boolean value, meaning that you can set them to either `true` or `false`.
 -->

UI 内の要素を有効化または無効化するだけの設定が、いくつかあります。これらのプロパティはそれぞれ真偽値を受け付けます。つまり、`true` または `false` のいずれかに設定できます。

<!-- 
Not every block will support every typography setting. Some are specific to a single block. For example, the `dropCap` property only works for Paragraph blocks. Others are widely used by almost any block with text, such as `customFontSize`.
 -->

すべてのブロックが、すべてのタイポグラフィ設定をサポートするわけではありません。一部の設定は、特定のブロックに限定されます。たとえば、`dropCap` プロパティは、「段落」ブロックでのみ機能します。一方、`customFontSize` のように、テキストを扱うほぼすべてのブロックで、広く使用されるものも存在します。

<!-- 
These `settings.typography` properties let you enable or disable features in the interface:
 -->

これらの `settings.typography` プロパティにより、インターフェースの機能を有効化または無効化できます:

<!-- 
*   **`customFontSize`:** Whether to let users input custom font sizes. Defaults to `true`.
*   **`dropCap`:** Whether users can enable a drop-cap for the first letter of the Paragraph block. Defaults to `true`.
*   **`fontStyle`:** Whether users can select a custom font style. Defaults to `true`.
*   **`fontWeight:`** Whether users can select a custom font weight. Weight ranges map to the standard **Thin** through **Black** font weights. Defaults to `true`.
*   **`letterSpacing`:** Whether users can input a custom letter spacing value. Defaults to `false`.
*   **`lineHeight`:** Whether users can input a custom line height for text. There is no way to register line-height presets, so this option enables a completely custom input. Defaults to `false`.
*   **`textColumns`:** Whether to show a columns option for the block’s text. Defaults to `false`.
*   **`textDecoration`:** Whether the user can set the text decoration for a block’s text. The available options are **None**, **Underline**, and **Strikethrough**. Defaults to `true`.
*   **`textTransform`:** Whether the user can change the letter case for a block’s text. The available options are **None**, **Uppercase**, **Lowercase**, and **Capitalize**. Defaults to `true`.
*   **`writingMode`:** Whether to enable the text **Orientation** in the interface, allowing users to choose between **Horizontal** and **Vertical** text. Defaults to `false`.
 -->

*   **`customFontSize`:** ユーザーが、カスタム・フォント・サイズを入力できるようにするか否かです。デフォルトは `true` です。
*   **`dropCap`:** 「段落」ブロックの最初の文字に対して、ドロップキャップを有効化できるか否かです。デフォルトは `true` です。
*   **`fontStyle`:** ユーザーが、カスタム・フォント・スタイルを選択できるか否かです。デフォルトは `true` です。
*   **`fontWeight:`** ユーザーが、カスタム・フォント・ウェイトを選択できるか否かです。ウェイト範囲は、標準の **細字** から **太字** に対応します。デフォルトは `true` です。
*   **`letterSpacing`:** ユーザーが、カスタム文字間隔値を入力できるか否かです。デフォルトは `false` です。
*   **`lineHeight`:** ユーザーが、カスタムの行高を入力できるか否かです。行高のプリセットを登録する方法がないため、このオプションは完全にカスタム入力が可能な状態にします。デフォルトは `false` です。
*   **`textColumns`:** ブロックのテキストに対して、カラム・オプションを表示するか否かです。デフォルトは `false` です。
*   **`textDecoration`:** ユーザーが、ブロックのテキストに対して、装飾を設定できるか否かです。利用可能なオプションは、**None**、**Underline**、**Strikethrough** です。デフォルトは `true` です。
*   **`textTransform`:** ユーザーが、ブロックのテキストに対して、文字の大文字/小文字を変更できるか否かです。利用可能なオプションは、**None**、**Uppercase**、**Lowercase**、および **Capitalize** です。デフォルトは `true` です。
*   **`writingMode`:** インターフェースで、テキストの **向き** を有効化するか否かです。これにより、ユーザーは **横書き** と **縦書き** のテキストを選択できます。デフォルトは `false` です。

<!-- 
Here is what these typography settings look like in the default WordPress `theme.json`:
 -->

以下は、デフォルトの WordPress `theme.json` における、これらのタイポグラフィ設定の表示例です:

```json
{
	"version": 2,
	"settings": {
		"typography": {
			"customFontSize": true,
			"dropCap": true,
			"fontStyle": true,
			"fontWeight": true,
			"letterSpacing": true,
			"lineHeight": false,
			"textColumns": false,
			"textDecoration": true,
			"textTransform": true,
			"writingMode": false
		}
	}
}
```

<!-- 
In this screenshot, take note of the **Typography** panel for the Paragraph block, which has every setting enabled:
 -->

このスクリーンショットでは、「段落」ブロックの **タイポグラフィ** パネルに注目してください。すべての設定が有効になっています:

<!-- 
[![WordPress post editor with a Heading and multiple Paragraph blocks inserted. In the right sidebar, nearly every typography option is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/10/typography-panel.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/typography-panel.jpg?ssl=1)
 -->

[![「見出し」と複数の「段落」ブロックが挿入された、WordPress 投稿エディター。右サイドバーでは、ほぼすべてのタイポグラフィ・オプションが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/typography-panel.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/typography-panel.jpg?ssl=1)

<!-- 
Depending on your theme’s audience, you will want to enable only the features that its users will need. For example, you may have a client who only needs to configure the font size. It wouldn’t make sense to show them every setting if it gets in the way of their workflow.
 -->

あなたのテーマのユーザー層に応じて、そのユーザーが必要とする機能のみを有効にする必要があります。たとえば、フォント・サイズの設定のみが必要なクライアントがいるかもしれません。彼らのワークフローの妨げになるなら、すべての設定を表示するのは意味がありません。

<!-- 
A note on drop caps: the current implementation feature is notoriously buggy with different font families, font sizes, and line heights. If you leave this feature enabled, be sure that you test that drop caps look good within your theme’s design. You may need to add custom CSS so that it matches your theme.
 -->

ドロップ・キャップに関する注意: 現在の実装機能は、異なるフォント・ファミリー、フォント・サイズ、行高で著しく不具合が生じやすいことが知られています。この機能を有効のままで使用する場合は、あなたのテーマのデザイン内でドロップ・キャップが適切に表示されることを必ずテストしてください。あなたのテーマに適合させるために、カスタム CSS を追加する必要があるかもしれません。

<!-- 
## Custom font families
 -->

## カスタム・フォント・ファミリー

<!-- 
WordPress lets you register as many font families as you want via the `settings.typography.fontFamilies` property in `theme.json`. You can add support for both system fonts (those that live on the visitor’s computer) or web fonts (custom fonts bundled with your theme). You’ll learn how to register both of these in this section.
 -->

WordPress では、`theme.json` 内の `settings.typography.fontFamilies` プロパティを介して、任意の数のフォント・ファミリーを登録できます。システムフォント (訪問者のコンピューターに存在するフォント) や Web フォント (あなたのテーマにバンドルされたカスタム・フォント) の両方をサポートするように追加できます。本セクションでは、これら両方の登録方法を学びます。

<!-- 
These appear as options under the **Typography > Font** field in the inspector panel for blocks that support selecting a font:
 -->

これらは、フォントの選択をサポートするブロックのインスペクタ・パネルの **タイポグラフィ > フォント** フィールド下にオプションとして表示されます:

<!-- 
[![WordPress post editor with a Cover block with inner blocks nested. In the sidebar, the Font dropdown is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-family.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-family.jpg?ssl=1)
 -->

[![内部ブロックがネストされた「カバー」ブロックが表示された、WordPress 投稿エディター。サイドバーでは、「フォント」ドロップダウンが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-family.jpg?resize=2048%2C1064&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-family.jpg?ssl=1)

<!-- 
The `settings.typography.fontFamilies` property is an empty array by default. You can register fonts by passing in font family objects with these properties:
 -->

デフォルトでは、`settings.typography.fontFamilies` プロパティは、空の配列です。以下のプロパティを持つフォント・ファミリー・オブジェクトを渡すことで、フォントを登録できます:

<!-- 
*   **`name`:** *(Required)* The human-readable title for the font family, which can be translated.
*   **`slug`:** *(Required)* The slug for the size, which will be appended to a generated CSS custom property: `--wp--preset--font-family--{slug}`.
*   **`fontFamily`:** *(Required)* A valid value that will map to the CSS `font-family` value. Generally, this will be a font stack (a list of families that the browser will try to use in order).
*   **`fontFace`:** *(Optional)* An array of font faces that are mapped to the `@font-face` CSS at-rule. You only need to use this when bundling custom web fonts with your theme.
 -->

*   **`name`:** *(必須)* 翻訳可能で、人間可読なフォント・ファミリーのタイトルです。
*   **`slug`:** *(必須)* 生成される CSS カスタム・プロパティに付加される、サイズのスラッグです: `--wp--preset--font-family--{slug}`。
*   **`fontFamily`:** *(必須)* CSS の `font-family` 値にマッピングされる、有効な値です。通常は、フォント・スタック (ブラウザーが順に使用を試みる、フォント・ファミリーのリスト) になります。
*   **`fontFace`:** *(任意)* CSS アットルール `@font-face` にマッピングされる、フォント・フェイスの配列です。あなたのテーマにカスタム Web フォントをバンドルする場合にのみ、これを使用する必要があります。

<!-- 
Here is what the font family setting looks like in the default WordPress `theme.json`:
 -->

以下は、デフォルトの WordPress `theme.json` における、フォント・ファミリーの設定例です:

```json
{
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": []
		}
	}
}
```

<!-- 
In the following subsections, you will first learn how to register system fonts. Then, you will take the next step and register a custom web font.
 -->

以下のサブ・セクションでは、まずシステム・フォントの登録方法を学びます。その後、次のステップとしてカスタム Web フォントを登録します。

<!-- 
### Registering system fonts
 -->

### システム・フォントの登録

<!-- 
System fonts are more straightforward than web fonts. You only need to know which fonts you want to use. For this exercise, let’s assume that you want to register two fonts that you will use in your theme:
 -->

システム・フォントは、Web フォントよりもシンプルです。使いたいフォントがどれかを知っていれば、十分です。このエクササイズでは、あなたのテーマで使用する2つのフォントを登録すると仮定しましょう:

<!-- 
*   **Primary:** a transitional serif font stack that will look good across modern devices.
*   **Secondary:** the user’s system UI font.
 -->

*   **Primary:** モダンなデバイスで美しく表示される、トランジショナルなセリフ・フォント・スタックです。
*   **Secondary:** ユーザーのシステム UI フォントです。

<!-- 
Add this code to your `theme.json` to register each of the fonts:
 -->

このコードをあなたの `theme.json` に追加して、各フォントを登録しましょう:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"name": "Primary",
					"slug": "primary",
					"fontFamily": "Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif"
				},
				{
					"name": "Secondary",
					"slug": "secondary",
					"fontFamily": "system-ui, sans-serif"
				}
			]
		}
	}
}
```

<!-- 
These options will now appear in the **Typography > Font** dropdown for any blocks that support the feature. 
 -->

これらのオプションは、この機能をサポートするブロックの **タイポグラフィ > フォント** ドロップダウンに表示されます。

<!-- 
WordPress will also generate two CSS custom properties with the `--wp--preset--font-family--{$slug}` format in both the editor and on the front end:
 -->

WordPress はまた、エディターとフロントエンドの両方で、`--wp--preset--font-family--{$slug}` フォーマットの2つの CSS カスタム・プロパティを生成します:

```css
body {
	--wp--preset--font-family--primary: Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif;
	--wp--preset--font-family--secondary: system-ui, sans-serif;
}
```

<!-- 
You can reference these as `var:preset|font-family|$slug` when you begin using them as [Styles in `theme.json`](https://developer.wordpress.org/themes/global-settings-and-styles/styles/). You can also reference them using `var( --wp--preset--font-family--{$slug} )` directly in CSS.
 -->

これらを [`theme.json` 内のスタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) として使用し始める際には、`var:preset|font-family|$slug` として参照できます。また、CSS 内で直接 `var( --wp--preset--font-family--{$slug} )` を使用しても参照できます。

<!-- 
It is generally recommended to use a semantic naming scheme for your font family slugs so that they are more future proof when switching between child themes, style variations, and even from theme to theme. These examples use `primary` and `secondary` since those are widely used terms. It’s best to avoid naming your slugs so that they match the current font family.
 -->

あなたのフォント・ファミリーのスラッグには、子テーマ間、スタイル・バリエーション間、さらにはテーマ間の切り替え時にも将来性を持たせるため、セマンティックな命名規則の使用が一般的に推奨されます。これらの例では、広く使用されている用語である `primary` と `secondary` を使用しています。あなたのスラッグの命名では、現在のフォント・ファミリーと同じ名前にしないことが最善です。

<!-- 
### Registering web fonts (font faces)
 -->

### Web フォント (フォント・フェイス) の登録

<!-- 
Registering custom web fonts works in much the same way as system fonts. The big difference is that you need to add the `fontFace` property to your font family objects.
 -->

カスタム Web フォントの登録は、システム・フォントとほぼ同様の方法で行います。主な違いは、あなたのフォント・ファミリー・オブジェクトに、`fontFace` プロパティを追加する必要がある点です。

<!-- 
`fontFace` must be an array of font face objects. Each object accepts these properties that map to descriptors for the [`@font-face` CSS at-rule](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face):
 -->

`fontFace` は、フォント・フェイス・オブジェクトの配列でなければなりません。各オブジェクトは、[CSS アットルール `@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face) の記述子に対応する、以下のプロパティを受け付けます:

<!-- 
*   **`fontFamily`:** A valid CSS `font-family` descriptor.
*   **`fontWeight`:** A range of CSS `font-weight` values.
*   **`fontStyle`:** A valid CSS `font-style` value.
*   **`fontStretch`:** A valid CSS font stretch value.
*   **`src`:** An array of font file URLs where the font files are located (this can be used to support multiple formats, but only one is required).
 -->

*   **`fontFamily`:** 有効な CSS `font-family` 記述子です。
*   **`fontWeight`:** CSS `font-weight` 値の範囲です。
*   **`fontStyle`:** 有効な CSS `font-style` 値です。
*   **`fontStretch`:** 有効な CSS フォント・ストレッチ値です。
*   **`src`:** フォント・ファイルが配置されている、フォント・ファイル URL の配列です (複数のフォーマットをサポートするために使用できるが、必須は1つだけ)。

<!-- 
The `src` property is unique in that it allows you to reference a URL that is relative to the `theme.json` file in your theme. Use the `"file:./path/to/file.ext"` format to reference a font bundled with your theme.
 -->

`src` プロパティは、あなたのテーマ内の `theme.json` ファイルに対する相対 URL を参照できる点でユニークです。あなたのテーマにバンドルされたフォントを参照するには、`"file:./path/to/file.ext"` フォーマットを使用してください。

<!-- 
Let’s try an example. Building off the code from the previous section, suppose you wanted to replace the system UI font with the Open Sans web font. 
 -->

例を見てみましょう。前セクションのコードをもとに、システム UI フォントを Open Sans Web フォントに置き換えたいとします。

<!-- 
This example will also assume you have downloaded and converted the Open Sans font to the modern `.woff2` format, which is widely supported by most browsers. You’ve also placed these files in your theme’s `/assets/fonts` folder like this:
 -->

この例では、Open Sans フォントをダウンロードし、ほとんどのブラウザーで広くサポートされている、最新の `.woff2` フォーマットに変換済みであることも前提とします。また、以下の通り、これらのファイルをあなたのテーマの `/assets/fonts` フォルダーに配置済みであることも前提とします:

*   `/assets`
    *   `/fonts`
        *   `/open-sans.woff2`
        *   `/open-sans-italic.woff2`

<!-- 
With your web fonts bundled in your theme and ready to go, add this code to your `theme.json` file to register them:
 -->

あなたのテーマにあなたの Web フォントがバンドルされ、すぐに使える状態になったら、このコードをあなたの `theme.json` ファイルに追加して登録しましょう:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fontFamilies": [
				{
					"name": "Primary",
					"slug": "primary",
					"fontFamily": "Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif"
				},
				{
					"name": "Secondary",
					"slug": "secondary",
					"fontFamily": "'Open Sans', sans-serif",
					"fontFace": [
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "normal",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/open-sans.woff2" ]
						},
						{
							"fontFamily": "Open Sans",
							"fontWeight": "300 800",
							"fontStyle": "italic",
							"fontStretch": "normal",
							"src": [ "file:./assets/fonts/open-sans-italic.woff2" ]
						}
					]
				}
			]
		}
	}
}
```

<!-- 
Like with system fonts, WordPress will generate CSS custom properties for web fonts. Here is what the CSS output looks like:
 -->

システム・フォントと同様に、WordPress は Web フォント用に CSS カスタム・プロパティを生成します。以下は、生成される CSS の出力例です:

```css
body {
	--wp--preset--font-family--primary: Charter, 'Bitstream Charter', 'Sitka Text', Cambria, serif;
	--wp--preset--font-family--secondary: 'Open Sans', sans-serif;
}
```

<!-- 
## Custom font sizes
 -->

## カスタム・フォント・サイズ

<!-- 
WordPress lets you register any number of preset font sizes that your theme users can choose from. By registering custom sizes, you can more easily maintain consistent typography across the theme.  
Custom font sizes appear as options in the **Typography > Size** panel in the inspector controls for blocks that support the feature:
 -->

WordPress では、あなたのテーマユーザーが選択できる、プリセット・フォント・サイズをいくつでも登録できます。カスタム・サイズを登録することで、テーマ全体で一貫したタイポグラフィを、より簡単に維持できます。
カスタム・フォント・サイズは、この機能をサポートするブロックのインスペクタ・コントロール内にある **タイポグラフィ > サイズ** パネルにオプションとして表示されます:

<!-- 
[![WordPress post editor showing multiple paragraphs with different font sizes.](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-sizes.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-sizes.jpg?ssl=1)
 -->

[![異なるフォント・サイズの段落が複数表示されている、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-sizes.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/font-sizes.jpg?ssl=1)

<!-- 
Note that if you have more than five custom sizes, the UI will show a dropdown select instead of the button group shown in the above screenshot.
 -->

カスタム・サイズが5つを超える場合、UI には上記のスクリーンショットに示されているボタングループではなく、ドロップダウンが表示されます。

<!-- 
There are two `theme.json.settings.typography` sub-properties related font sizes:
 -->

フォント・サイズに関連する2つの `theme.json.settings.typography` サブプロパティがあります:

<!-- 
*   **`fluid`:** Whether to enable fluid font sizes that scale up on large screens and down on smaller screens. This can be overridden for individual custom sizes. Defaults to `false`.
*   **`fontSizes`:** An array of font size objects that you can use to customize the available presets that users can choose from. WordPress registers the default sizes of `small`, `medium`, `large`, and `x-large`.
 -->

*   **`fluid`:** 大きな画面では拡大し、小さな画面では縮小するフルード・フォント・サイズを有効にするか否かです。これはそれぞれのカスタム・サイズで上書きできます。デフォルトは `false` です。
*   **`fontSizes`:** ユーザーが選択できるプリセットをカスタマイズするために使用できる、フォント・サイズ・オブジェクトの配列です。WordPress は、デフォルトで `small`、`medium`、`large`、`x-large` のサイズを登録します。

<!-- 
Here is what these properties look like in the default WordPress `theme.json`:
 -->

以下は、デフォルトの WordPress `theme.json` における、これらのプロパティの表示例です:

```json
{
	"version": 2,
	"settings": {
		"typography": {
			"fluid": false,
			"fontSizes": [
				{
					"name": "Small",
					"slug": "small",
					"size": "13px"
				},
				{
					"name": "Medium",
					"slug": "medium",
					"size": "20px"
				},
				{
					"name": "Large",
					"slug": "large",
					"size": "36px"
				},
				{
					"name": "Extra Large",
					"slug": "x-large",
					"size": "42px"
				}
			]
		}
	}
}
```

<!-- 
As you can see, WordPress disables fluid font sizes by default and registers four static sizes of its own. In almost all cases, you will want to overwrite these with sizes that match your theme’s design.
 -->

ご覧の通り、WordPress はデフォルトでフルード・フォント・サイズを無効化し、独自の4つの静的サイズを登録します。ほとんどの場合、あなたのテーマのデザインに適合するサイズでこれらを上書きしたいでしょう。

<!-- 
Like other presets that you can set in `theme.json`, WordPress automatically generates CSS custom properties for font sizes using the `--wp--preset--font-size--{$slug}` format. For the default sizes, this CSS is output in the editor and on the front end:
 -->

`theme.json` で設定できる他のプリセットと同様に、WordPress はフォント・サイズに対して、`--wp--preset--font-size--{$slug}` フォーマットで CSS カスタム・プロパティを自動生成します。デフォルト・サイズの場合、この CSS はエディターとフロントエンドで以下のように出力されます:

```css
body {
	--wp--preset--font-size--small: 13px;
	--wp--preset--font-size--medium: 20px;
	--wp--preset--font-size--large: 36px;
	--wp--preset--font-size--x-large: 42px;
}
```

<!-- 
WordPress also generates custom CSS classes for each font size preset using the `.has-{$slug}-font-size` naming scheme. The default sizes produce these classes:
 -->

WordPress はまた、各フォントサイズプリセットに対して、`.has-{$slug}-font-size` 命名規則を用いたカスタム CSS クラスを生成します。デフォルトのサイズでは、以下のクラスが生成されます:

```css
.has-small-font-size{
	font-size: var(--wp--preset--font-size--small) !important;
}

.has-medium-font-size{
	font-size: var(--wp--preset--font-size--medium) !important;
}

.has-large-font-size{
	font-size: var(--wp--preset--font-size--large) !important;
}

.has-x-large-font-size{
	font-size: var(--wp--preset--font-size--x-large) !important;
}
```

<!-- 
### Enabling fluid typography
 -->

### フルード・タイポグラフィの有効化

<!-- 
In modern web design, you will almost always utilize fluid typography. This allows your font sizes to scale up or down with the viewport or container.
 -->

モダン Web デザインでは、ほぼ必ずフルード・タイポグラフィを適用します。これにより、あなたのフォント・サイズはビューポートやコンテナに合わせて拡縮されます。

<!-- 
WordPress uses a viewport-based system for fluid typography. But you don’t have to rely on this if you prefer to use something different, such as a container-based system, and can leave it disabled.
 -->

WordPress はフルード・タイポグラフィのために、ビューポートベースのシステムを採用しています。ただし、コンテナ・ベースのシステムなど別の方法を使用したい場合は、このシステムに依存する必要はなく、無効にしておくことも可能です。

<!-- 
Suppose you wanted to use the default core sizes but wanted them all to be fluid instead of static values. You can enable this by setting `settings.typography.fluid` to `true` in your `theme.json` file:
 -->

デフォルトのコア・サイズを使用したいが、静的な値ではなくすべてフルード・サイズにしたい、としましょう。あなたの `theme.json` ファイルで `settings.typography.fluid` を `true` に設定することで、これを有効にできます:

```json
{
	"version": 2,
	"settings": {
		"typography": {
			"fluid": true
		}
	}
}
```

<!-- 
WordPress will now generate fluid sizes for registered font sizes:
 -->

WordPress は登録されたフォント・サイズに対して、フルード・サイズを自動生成します:

```css
body {
	--wp--preset--font-size--small: 13px;
	--wp--preset--font-size--medium: clamp(14px, 0.875rem + ((1vw - 3.2px) * 0.852), 20px);
	--wp--preset--font-size--large: clamp(22.041px, 1.378rem + ((1vw - 3.2px) * 1.983), 36px);
	--wp--preset--font-size--x-large: clamp(25.014px, 1.563rem + ((1vw - 3.2px) * 2.413), 42px);
}
```

<!-- 
`14px` is the default minimum font-size limit. Because the `small` size is below that limit, it remained at its static size of `13px`.
 -->

`14px` は、デフォルトの最小フォント・サイズ制限です。`small` サイズはこの制限を下回っているため、静的なサイズである `13px` のまま維持されました。

<!-- 
### Registering custom font size presets
 -->

### カスタム・フォント・サイズ・プリセットの登録

<!-- 
You will undoubtedly want to register font sizes that match your theme’s design instead of sticking with the defaults. To do this, you must pass an array of font size objects to the `settings.typography.fontSizes` property in `theme.json`.
 -->

あなたのテーマのデザインに適合するフォント・サイズの登録をおすすめします。デフォルトのままにしておくのではなく、必ず登録してください。これを行うには、`theme.json` 内の `settings.typography.fontSizes` プロパティに、フォント・サイズ・オブジェクトの配列を渡す必要があります。

<!-- 
Each of these objects accepts several properties:
 -->

これらのオブジェクトはそれぞれ、複数のプロパティを受け入れます:

<!-- 
*   **`name`:** The human-readable title for the size, which can be translated.
*   **`size`:** A valid CSS size. This can be a number and unit, a custom fluid size using `clamp()`, or a reference to another custom CSS property.
*   **`slug`:** The slug for the size, which will be appended to a generated CSS custom property: `--wp--preset--spacing--{slug}`.
*   **`fluid`:** A boolean value to enable or disable fluid typography for this specific size, overwriting the global property. Alternatively, it can be an object containing:
    *   **`min`:** The minimum value that the font size can scale down to. Must be a valid CSS size.
    *   **`max`:** The maximum value that the font size can scale up to. Must be a valid CSS size.
 -->

*   **`name`:** 翻訳可能で、人間可読なサイズのタイトルです。
*   **`size`:** 有効な CSS サイズです。数値と単位、`clamp()` を使用したカスタム・フルード・サイズ、または別のカスタム CSS プロパティへの参照が可能です。
*   **`slug`:** 生成される CSS カスタム・プロパティに付加される、サイズのスラッグです: `--wp--preset--spacing--{slug}`.
*   **`fluid`:** この特定のサイズに対してフルード・タイポグラフィを有効/無効にする真偽値で、グローバル・プロパティを上書きします。あるいは、以下のオブジェクトを含めることもできます:
    *   **`min`:** フォント・サイズがスケール・ダウンできる最小値です。有効な CSS サイズである必要があります。
    *   **`max`:** フォント・サイズがスケール・アップできる最大値です。有効な CSS サイズである必要があります。

<!-- 
Let’s register a simple set of custom sizes with static values first. Add this code to your `theme.json` file:
 -->

まず、静的値を持つシンプルなカスタム・サイズのセットを登録しましょう。このコードをあなたの `theme.json` ファイルに追加しましょう:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fontSizes": [
				{
					"name": "Small",
					"size": "1rem",
					"slug": "sm"
				},
				{
					"name": "Medium",
					"size": "1.25rem",
					"slug": "md"
				},
				{
					"name": "Large",
					"size": "1.5rem",
					"slug": "lg"
				}
			]
		}
	}
}
```

<!-- 
Just like with the default size presets, WordPress will automatically generate the CSS for each in both the editor and on the front end:
 -->

デフォルトのサイズ・プリセットと同様に、WordPress は、エディターとフロントエンドの両方で、それぞれに対して CSS を自動的に生成します:

```css
body {
	--wp--preset--font-size--sm: 1rem;
	--wp--preset--font-size--md: 1.25rem;
	--wp--preset--font-size--lg: 1.5rem;
}
```

<!-- 
Now, let’s take this one step further. In the previous example, you registered Small, Medium, and Large sizes. Suppose that you wanted the Small size to maintain its value regardless of the browser’s viewport width. But you want the Medium and Large size to scale along with the viewport.
 -->

では、さらに一歩進んでみましょう。前の例では、Small、Medium、Large のサイズを登録しました。ブラウザーのビューポート幅に関係なく、Small サイズの値を維持したいとしましょう。一方、Medium と Large サイズは、ビューポートに合わせて拡大縮小させたい、としましょう。

<!-- 
Using the `fluid` property, let’s configure these on a size-by-size basis. Add this code to your `theme.json`:
 -->

`fluid` プロパティを使用して、サイズごとにこれらを設定しましょう。あなたの `theme.json` に、このコードを追加しましょう:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"typography": {
			"fluid": true,
			"fontSizes": [
				{
					"name": "Small",
					"size": "1rem",
					"slug": "sm",
					"fluid": false
				},
				{
					"name": "Medium",
					"size": "1.25rem",
					"slug": "md",
					"fluid": {
						"min": "1rem",
						"max": "1.5rem"
					}
				},
				{
					"name": "Large",
					"size": "1.5rem",
					"slug": "lg",
					"fluid": {
						"min": "1.25rem",
						"max": "2rem"
					}
				}
			]
		}
	}
}
```

<!-- 
WordPress will generate these CSS custom properties:
 -->

WordPress は、これらの CSS カスタム・プロパティを生成します:

```css
body {
	--wp--preset--font-size--sm: 1rem;
	--wp--preset--font-size--md: clamp(1rem, 1rem + ((1vw - 0.2rem) * 1.136), 1.5rem);
	--wp--preset--font-size--lg: clamp(1.25rem, 1.25rem + ((1vw - 0.2rem) * 1.705), 2rem);
}
```

<!-- 
There aren’t many limits to how you can customize this for your theme. The above offers an intro to registering custom font sizes, but you have full control over how this works for your theme.
 -->

あなたのテーマに合わせてこれをカスタマイズする方法には、ほとんど制限がありません。上記はカスタム・フォント・サイズの登録方法の概要ですが、あなたのテーマでの動作については、完全にコントロール可能です。

<!-- 
For a deeper understanding of fluid font sizes, read [Intrinsic design, theming, and rethinking how to design with WordPress](https://developer.wordpress.org/news/2023/02/intrinsic-design-theming-and-rethinking-how-to-design-with-wordpress/) on the Developer Blog.
 -->

フルード・フォント・サイズについて、より深く理解したい場合は、開発者ブログの [WordPress を用いた本質的なデザイン、テーマ設定、そしてデザイン手法の再考](https://developer.wordpress.org/news/2023/02/intrinsic-design-theming-and-rethinking-how-to-design-with-wordpress/) をご覧ください。