<!-- 
# Using Presets
 -->

# プリセットの使用

<!-- 
In the `theme.json` [Settings documentation](https://developer.wordpress.org/themes/global-settings-and-styles/settings), you learned how to register custom presets, such as a color palette, font sizes, a spacing scale, and more. In the [Styles documentation](https://developer.wordpress.org/themes/global-settings-and-styles/styles/), you’ve learned how to apply CSS styles via `theme.json`.
 -->

`theme.json` [設定ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/settings) では、カラーパレット、フォントサイズ、間隔スケールなどのカスタム・プリセットを登録する方法を学びました。[スタイル・ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/styles/) では、`theme.json` を介して CSS スタイルを適用する方法を学びました。

<!-- 
Now it’s time to combine these two concepts by applying styles using the presets that you’ve registered.
 -->

それでは、登録したプリセットを使用してスタイルを適用することで、これら2つの概念を組み合わせるときが来ました。

<!-- 
In the styles documentation, you will often see examples using hard-coded CSS values. This is primarily for the sake of demonstration. You will almost always use registered presets instead. This makes it much easier to manage everything from a single location.
 -->

スタイル・ドキュメントでは、ハードコードされた CSS 値を使用した例がよく見られます。これは主に説明のためです。実際には、登録済みのプリセットを使用することがほとんどです。これにより、すべてを一ヵ所で管理することが格段に容易になります。

<!-- 
## What are presets?
 -->

## プリセットって ?

<!-- 
Essentially, presets are options that you register—generally for users to select from the UI—that map to CSS custom properties.
 -->

基本的に、プリセットとはあなたが登録するオプションで — 通常はユーザーが UI から選択するためのもので — CSS カスタム・プロパティに対応するものです。

<!-- 
For example, when you learned how to [register custom font sizes](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/), you added your presets to `settings.typography.fontSizes`. WordPress takes each of those font sizes and creates a CSS custom property with the name of `--wp--preset--font-size–{$slug}`.
 -->

たとえば、[カスタム・フォント・サイズの登録](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) 方法を学んだ際、あなたのプリセットを `settings.typography.fontSizes` に追加しました。WordPress はそれらのフォントサイズそれぞれを取り込み、`--wp--preset--font-size–{$slug}` という名前で CSS カスタム・プロパティを作成します。

<!-- 
WordPress itself, your theme, plugins, and even users can register presets for the various features that are supported. And WordPress creates CSS custom properties for all registered presets with the name of `--wp--preset–{$feature}-{$slug}`.
 -->

WordPress 自身、あなたのテーマ、プラグイン、さらにはユーザーまでもが、サポートされているさまざまな機能に対して、プリセットを登録できます。そして WordPress は、登録されたすべてのプリセットに対して、`--wp--preset–{$feature}-{$slug}` という名前で CSS カスタムプロパティを作成します。

<!-- 
Let’s look at a basic example of a [custom color palette](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/) with three colors:
 -->

3色からなる [カスタム・カラーパレット](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/) の基本的な例を見てみましょう:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"palette": [
				{
					"color": "#ffffff",
					"name": "Base",
					"slug": "base"
				},
				{
					"color": "#000000",
					"name": "Contrast",
					"slug": "contrast"
				},
				{
					"color": "#89cff0",
					"name": "Primary",
					"slug": "primary"
				}
			]
		}
	}
}
```

<!-- 
This creates three CSS custom properties, which WordPress will output in the editor and on the front end:
 -->

これにより3つの CSS カスタム・プロパティが生成され、WordPress は、エディターとフロントエンドで、以下を出力します:

```css
body {
	--wp--preset--color--base: #ffffff;
	--wp--preset--color--contrast: #000000;
	--wp--preset--color--primary: #89cff0;
}
```

<!-- 
At the end of the day, presets are merely a standardized method of creating options in the interface and generating CSS custom properties.
 -->

結局のところ、プリセットとは、インターフェース内でオプションを作成し、CSS カスタム・プロパティを生成するための標準化された手法に過ぎません。

<!-- 
## Applying presets as styles
 -->

## スタイルとしての、プリセットの適用

<!-- 
Because presets are registered as settings, they are available to select in the user interface. But you must apply them as styles if you want to use them as part of your theme’s default design.
 -->

プリセットは設定として登録されるため、UI で選択可能です。ただし、あなたのテーマのデフォルト・デザインの一部として使用したい場合は、スタイルとして適用する必要があります。

<!-- 
Let’s build off the custom color palette from the previous section. Suppose you wanted to apply these styles using your registered presets:
 -->

前のセクションで作成したカスタム・カラーパレットをもとに、構築しましょう。あなたの登録済みプリセットを使用して、これらのスタイルを適用したいとしましょう:

<!-- 
*   The site’s background color should use the `base` preset.
*   The site’s primary text color should use the `contrast` preset.
*   Link colors should use the `primary` preset.
 -->

*   サイトの背景色は、`base` プリセットを使用してください。
*   サイトの主テキスト色は、`contrast` プリセットを使用してください。
*   リンク色は、`primary` プリセットを使用してください。

<!-- 
To reference presets in `theme.json`, there is a special syntax that you can use: `var:preset|$feature|$slug`. So `base` color in this instance would be `var:preset|color|base`.
 -->

`theme.json` でプリセットを参照する場合、特別な構文を使用できます: `var:preset|$feature|$slug`。したがって、この場合の `base` カラーは `var:preset|color|base` となります。

<!-- 
With that plan in mind and using what you’ve already learned from this chapter, try your hand at recreating this in `theme.json`. Your code should look like this:
 -->

この計画を念頭に置き、本章ですでに学んだことを活用して、`theme.json` でこれを再現してみてください。あなたのコードは次のようになるはずです:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"palette": [
				{
					"color": "#ffffff",
					"name": "Base",
					"slug": "base"
				},
				{
					"color": "#000000",
					"name": "Contrast",
					"slug": "contrast"
				},
				{
					"color": "#89cff0",
					"name": "Primary",
					"slug": "primary"
				}
			]
		}
	},
	"styles": {
		"color": {
			"text": "var:preset|color|contrast",
			"background": "var:preset|color|base"
		},
		"elements": {
			"link": {
				"color": {
					"text": "var:preset|color|primary"
				}
			}
		}
	}
}
```

<!-- 
If you test your site on the front end or via the editor, you should see that your colors have correctly applied:
 -->

フロントエンドまたはエディター経由であなたのサイトをテストすると、あなたの色が正しく適用されていることが確認できるはずです:

<!-- 
[![WordPress post editor with a couple of demo paragraphs. The image reflects the black text color and blue link color.](https://i0.wp.com/developer.wordpress.org/files/2023/10/using-presets-color.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/using-presets-color.jpg?ssl=1)
 -->

[![デモ用段落がいくつか並んだ、WordPress 投稿エディター。画像は、黒のテキスト色と青のリンク色を反映している。](https://i0.wp.com/developer.wordpress.org/files/2023/10/using-presets-color.jpg?resize=2048%2C1056&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/using-presets-color.jpg?ssl=1)

<!-- 
The next step now is to figure out which elements and blocks you want to apply other presets to. Depending on the complexity of your theme, this can be as simple as a few custom colors to hundreds of lines of JSON code. Really, what you do from here is entirely up to you.
 -->

次に、どの要素やブロックに他のプリセットを適用したいかを決める必要があります。あなたのテーマの複雑さによっては、これは数種類のカスタムカラーから数百行の JSON コードまで、その範囲はさまざまです。ここから先は、本当に何をしてもかまいません。

<!-- 
Technically, you can reference presets using the CSS syntax of `var( --wp--preset--{$feature}--{$slug} )`. But the WordPress `var:preset|$feature|$slug` syntax works much better and always appears correctly throughout the interface in the WordPress admin. Save the CSS syntax for when you are actually writing CSS.
 -->

技術的には、プリセットを `var( --wp--preset--{$feature}--{$slug} )` という CSS 構文で参照できます。しかし WordPress の `var:preset|$feature|$slug` 構文の方がはるかに優れており、WordPress 管理画面のインターフェース全体で常に正しく表示されます。CSS 構文は、実際に CSS を記述する際に取っておきましょう。

<!-- 
### Referencing custom presets
 -->

### カスタム・プリセットの参照

<!-- 
In the [Custom Settings](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/) documentation, you learned how to create “custom” presets. These are non-standard CSS custom properties that you can register, and WordPress generates the CSS output for you.
 -->

[カスタム設定](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/) ドキュメントでは、「カスタム」プリセットの作成方法を学びました。これらは登録可能な非標準の CSS カスタム・プロパティであり、WordPress が CSS 出力を生成します。

<!-- 
These use a different naming convention in comparison to standard presets. Essentially, whenever you used the term `preset` in your code for standard presets, you would exchange that for `custom` when dealing with custom presets.
 -->

これらは標準プリセットと比べて、異なる命名規則を採用しています。基本的に、あなたのコードで標準プリセットに対して `preset` という用語を使用していた箇所は、カスタム・プリセットを扱う際には `custom` に置き換えることになります。

<!-- 
Let’s walk through an example. Assume that you wanted to register some CSS custom properties for handling line heights in your theme design. You would add this to your `theme.json` file:
 -->

例を見てみましょう。あなたのテーマデザインで行高を扱うために、いくつかの CSS カスタム・プロパティを登録したいとしましょう。あなたの `theme.json` ファイルに以下を追加します:

```json
{
	"version": 2,
	"settings": {
		"custom": {
			"lineHeight": {
				"xs": "1",
				"sm": "1.25",
				"md": "1.5",
				"lg": "1.75"
			}
		}
	}
}
```

<!-- 
WordPress will generate these custom line heights as CSS custom properties in the editor and on the front end:
 -->

WordPress は、これらのカスタム行高を CSS カスタム・プロパティとして、エディターとフロントエンドの両方で生成します:

```css
body {
	--wp--custom--line-height--xs: 1;
	--wp--custom--line-height--sm: 1.25;
	--wp--custom--line-height--md: 1.5;
	--wp--custom--line-height--lg: 1.75;
}
```

<!-- 
To reference these as styles in `theme.json`, you would use the `var:custom` syntax instead of `var:preset`.
 -->

これらを `theme.json` 内でスタイルとして参照するには、`var:preset` ではなく `var:custom` 構文を使用します。

<!-- 
Suppose you wanted to apply the registered `md` line-height size as the default line height at the root/global level. For that, you would need to target `styles.typography.lineHeight`.
 -->

ルート/グローバル・レベルで、デフォルトの行高として、登録済みの `md` 行高サイズを適用したい場合を考えましょう。そのためには、`styles.typography.lineHeight` をターゲットにする必要があります。

<!-- 
Here is what the full code would look like in `theme.json`:
 -->

`theme.json` 内の完全なコードは以下のようになります:

```
{
	"version": 2,
	"settings": {
		"custom": {
			"lineHeight": {
				"xs": "1",
				"sm": "1.25",
				"md": "1.5",
				"lg": "1.75"
			}
		}
	},
	"styles": {
		"typography": {
			"lineHeight": "var:custom|line-height|md"
		}
	}
}
```

<!-- 
Of course, you could use your other custom line-height presets for styling other elements and blocks.
 -->

もちろん、あなたの他のカスタム行高プリセットを使って、他の要素やブロックのスタイルも設定できます。

<!-- 
## Available presets
 -->

## 利用可能なプリセット

<!-- 
WordPress has several features that you can register presets for. You can find these presets in their corresponding settings docs (the specific properties are noted in parentheses):
 -->

WordPress には、プリセットを登録できる機能がいくつかあります。これらのプリセットは、対応する設定ドキュメントで確認できます (具体的なプロパティは括弧内に記載):

<!-- 
*   [Color](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/) (`palette`)
*   [Shadow](https://developer.wordpress.org/themes/global-settings-and-styles/settings/shadow/) (`presets`)
*   [Spacing](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/) (`spacingScale`, `spacingSizes`)
*   [Typography](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) (`fontSizes`, `fontFamily`)
*   [Custom](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/)
 -->

*   [色](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color/) (`palette`)
*   [影](https://developer.wordpress.org/themes/global-settings-and-styles/settings/shadow/) (`presets`)
*   [間隔](https://developer.wordpress.org/themes/global-settings-and-styles/settings/spacing/) (`spacingScale`, `spacingSizes`)
*   [タイポグラフィ](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) (`fontSizes`, `fontFamily`)
*   [カスタム](https://developer.wordpress.org/themes/global-settings-and-styles/settings/custom/)