<!-- 
# Blocks
 -->

# ブロック

<!-- 
Most settings in `theme.json` let you configure properties at the global level. This means that they apply to all blocks that support them. But WordPress also lets you control this at the block level.
 -->

`theme.json` のほとんどの設定では、グローバル・レベルでプロパティを構成できます。これは、それらをサポートするすべてのブロックに適用されることを意味します。ただし WordPress では、ブロックレベルでもこれを制御できます。

<!-- 
That’s what the `settings.block` property is for—you can configure everything from typography, to colors, to spacing, and more for individual blocks.
 -->

それが `settings.block` プロパティの役割です — 個々のブロックごとに、タイポグラフィから色、間隔設定など、あらゆる要素を構成できます。

<!-- 
Before moving forward with this page of the handbook, it is important to familiarize yourself with at least some of the existing [`theme.json` settings](https://developer.wordpress.org/themes/global-settings-and-styles/settings/). This way, you can apply them on a per-block basis.
 -->

このハンドブックのページを進める前に、既存の [`theme.json` 設定](https://developer.wordpress.org/themes/global-settings-and-styles/settings/) の少なくとも一部に慣れることが重要です。そうすることで、ブロック単位でそれらを適用できます。

<!-- 
## How block settings work
 -->

## ブロック設定のしくみ

<!-- 
In the previous pages of the `theme.json` settings documentation, you learned how to configure specific properties at the global level. Essentially, this means that they are applied to all blocks that support the specific property/feature.
 -->

`theme.json` 設定ドキュメントの前のページでは、グローバル・レベルで特定のプロパティを設定する方法について学びました。本質的に、これは特定のプロパティ/機能をサポートするすべてのブロックに適用されることを意味します。

<!-- 
You would have configured many of these properties in your `theme.json` (shortened for example—you can review all available properties via the main [settings documentation](https://developer.wordpress.org/themes/global-settings-and-styles/settings/)):
 -->

これらのプロパティの多くは、あなたの `theme.json` で設定済みでしょう (例として簡略化 — 利用可能な全プロパティは、メインの [設定ドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/settings/) でご覧あれ):

```json
{
	"version": 2,
	"settings": {
		"border": {},
		"color": {},
		"custom": {},
		"spacing": {},
		"typography": {}
	}
}
```

<!-- 
But there are times when you need to add settings at the individual block level, and anything set for the block will overrule its global setting. So let’s explore an example that shows block-specific settings overwriting the global settings.
 -->

ただし、個々のブロックレベルで設定を追加する必要がある場合もあり、ブロックに設定された内容はグローバル設定を上書きします。では、ブロック固有の設定がグローバル設定を上書きする例を見てみましょう。

<!-- 
For this example, you will create a custom color palette, which you can learn about in the [color settings documentation](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color). This will be applied globally and used for every block’s color picker. Then, you will create a custom color palette for the Cover block that’s only shown for the Cover block.
 -->

この例では、カスタム・カラーパレットを作成します。詳細は [カラー設定のドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/settings/color) でご確認ください。このパレットはグローバルに適用され、すべてのブロックの色選択ツールで使用されます。では、「カバー」ブロック専用に表示されるカスタム・カラーパレットを作成しましょう。

<!-- 
First, add your global color palette in `theme.json` with two colors named `base` and `contrast`:
 -->

まず、`theme.json` にあなたのグローバル・カラーパレットを追加し、`base` と `contrast` という名前の2色を定義します:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"palette": [
				{
					"color": "#0284c7",
					"name": "Base",
					"slug": "base"
				},
				{
					"color": "#ffffff",
					"name": "Contrast",
					"slug": "contrast"
				}
			]
		}
	}
}
```

<!-- 
Now add a Cover block and some nested text in the WordPress editor, saving the **Text** and **Overlay** colors for the block to your two custom colors:
 -->

では、WordPress エディターに「カバー」ブロックとネストされたテキストを追加し、ブロックの **テキスト** と **オーバーレイ** 色をあなたの2つのカスタム・カラーに保存しましょう:

<!-- 
[![WordPress post editor showing a Cover block with a blue background and white text.](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-global-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-global-colors.jpg?ssl=1)
 -->

[![青色の背景に白い文字の「カバー」ブロックを表示している、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-global-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-global-colors.jpg?ssl=1)

<!-- 
As you can see, the Cover block currently uses the global color palette that you configured in your `theme.json` file.
 -->

ご覧の通り、「カバー」ブロックは現在、あなたの `theme.json` ファイルで設定したグローバル・カラーパレットを使用しています。

<!-- 
Suppose that you wanted the Cover block to use an orange color palette. You can configure that by targeting `settings.blocks[core/cover].color.palette` in your `theme.json` file and passing an array of custom colors.
 -->

「カバー」ブロックにオレンジ色のカラーパレットを使用させたい、としましょう。あなたの `theme.json` ファイル内で `settings.blocks[core/cover].color.palette` を指定し、カスタム・カラーの配列を渡すことで設定できます。

<!-- 
Add this new section to your existing `theme.json` so that it looks like this:
 -->

あなたの既存の `theme.json` に、この新しいセクションを追加し、以下のようにしてください:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"palette": [
				{
					"color": "#0284c7",
					"name": "Base",
					"slug": "base"
				},
				{
					"color": "#ffffff",
					"name": "Contrast",
					"slug": "contrast"
				}
			]
		}
		"blocks": {
			"core/cover": {
				"color": {
					"palette": [
						{
							"color": "#ea580c",
							"name": "Base",
							"slug": "base"
						},
						{
							"color": "#fff7ed",
							"name": "Contrast",
							"slug": "contrast"
						}
					]
				}
			}
		}
	}
}
```

<!-- 
As shown in the `theme.json` example, you use the same organizational structure for block settings as you do for global settings (i.e., `settings.color` at the global level but `settings.blocks[core/cover].color` at the block level).
 -->

`theme.json` の例に示すように、ブロック設定にはグローバル設定と同じ構造を使用します (つまり、グローバル・レベルでは `settings.color` ですが、ブロック・レベルでは `settings.blocks[core/cover].color` となります)。

<!-- 
If you refresh your browser window, your Cover block should now show the new colors:
 -->

あなたのブラウザーのウィンドウを更新すると、あなたの「カバー」ブロックは新しい色を表示するはずです:

<!-- 
[![WordPress post editor showing a Cover block with an orange background and white text.](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-block-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-block-colors.jpg?ssl=1)
 -->

[![オレンジ色の背景に白い文字の「カバー」ブロックを表示している、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-block-colors.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/cover-block-colors.jpg?ssl=1)

<!-- 
If you check other blocks, they will still use the global color palette. Only the Cover block will use this custom orange palette.
 -->

他のブロックを確認すると、それらは依然としてグローバル・カラーパレットを使用したままです。「カバー」ブロックのみがこのカスタム・オレンジ・パレットを使用します。

<!-- 
Per-block color palettes are just the tip of the iceberg. You can configure any `theme.json` for any block (assuming the block supports it). This gives you an incredible amount of control over how your theme works.
 -->

ブロックごとのカラーパレットは、氷山の一角に過ぎません。(ブロックが対応している場合) 任意のブロックに対して、任意の `theme.json` を設定できます。これにより、あなたのテーマの動作を驚くほど細かく制御できます。

<!-- 
When targeting a block’s settings, you must know both its namespace and slug. Above, you learned that the Cover block has the namespace (`core`) and slug (`cover`), creating the namespace/slug combination of `core/cover`. All core WordPress blocks have the `core` namespace, and you can find this information for any block (including from third-party plugins) in its `block.json` file.
 -->

ブロックの設定を指定する際には、その名前空間とスラッグの両方を把握する必要があります。前述の通り、「カバー」ブロックは名前空間 (`core`) とスラッグ (`cover`) を持ち、これらが組み合わさって `core/cover` という名前空間/スラッグの組み合わせを形成します。すべてのコア WordPress ブロックは `core` 名前空間を持ち、この情報は (サードパーティ製プラグインのブロックも含む) 任意のブロックの `block.json` ファイルで確認できます。

<!-- 
## Default block settings
 -->

## デフォルトのブロック設定

<!-- 
Believe it or not, WordPress actually configures a couple of default block settings in `theme.json`. Generally, this would be left to themes, but these settings are primarily enabled for backward compatibility with features from older versions of WordPress.
 -->

信じられないかもしれませんが、WordPress は実際に `theme.json` でいくつかのデフォルトのブロック設定を構成しています。通常、これはテーマに任されるべきですが、これらの設定は主に、古いバージョンの WordPress の機能との下位互換性を確保するために有効化されています。

<!-- 
WordPress enables a few settings for the Button and Pullquote blocks by default. Here is what this looks like in the default `theme.json`:
 -->

WordPress では、「ボタン」ブロックと「プルクオート」ブロックに対して、デフォルトでいくつかの設定が有効になっています。デフォルトの `theme.json` では、以下のように記述されています:

```json
{
	"version": 2,
	"settings": {
		"blocks": {
			"core/button": {
				"border": {
					"radius": true
				}
			},
			"core/pullquote": {
				"border": {
					"color": true,
					"radius": true,
					"style": true,
					"width": true
				}
			}
		}
	}
}
```

<!-- 
You can overwrite these block-specific settings in your `theme.json` file just as you learned to do in the previous section of this documentation.
 -->

これらのブロック固有の設定は、このドキュメントの前のセクションで学んだ方法と同様に、あなたの `theme.json` ファイルで上書きできます。

<!-- 
If you are wondering why some of your global settings do not seem to apply to certain blocks, particularly Button and Pullquote, it is likely because they are being set at the block level. You will need to override these in `settings.blocks` in your `theme.json` if you want a different behavior.
 -->

あなたのグローバル設定の一部が特定のブロック (特に「ボタン」や「プルクオート」) に適用されていないように見える場合は、そのブロック・レベルで設定されているためです。異なる挙動を望む場合は、あなたの `theme.json` 内の `settings.blocks` でこれらの設定を上書きする必要があります。