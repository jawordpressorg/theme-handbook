<!-- 
# Color
 -->

# 色

<!-- 
Color is one of the primary components of design. You can create a theme that is dark and moody, fun and lighthearted, or clean and corporate. Which colors you choose will define how the world sees your theme, and WordPress provides a range of color-specific configuration options that you can set.
 -->

色は、デザインの主要な構成要素の一つです。暗くムーディーなテーマ、楽しく軽やかなテーマ、あるいはクリーンで企業向けのテーマを作成できます。選択する色によって、世界があなたのテーマをどう見るかが決まります。WordPress では、あなたが設定できる色に特化した、さまざまな設定オプションを提供しています。

<!-- 
The `settings.color`  property in `theme.json` gives you full control over how colors, gradients, and more work within your theme. Primarily, the goal is for configuring whether specific controls appear in the user interface, but it also lets you register custom presets that users can select.
 -->

`theme.json` 内の `settings.color` プロパティを使用すると、あなたのテーマ内で色やグラデーションなどがどのように機能するかを、完全に制御できます。主な目的は、特定のコントロールが UI に表示されるかどうかを設定することですが、ユーザーが選択できるカスタム・プリセットも登録できます。

<!-- 
## Color settings
 -->

## 色の設定

<!-- 
`color` is an object that’s nested directly within the top-level `settings` property in `theme.json`. It is used to configure multiple color-specific settings that appear in the user interface.
 -->

`color` は、`theme.json` の最上位プロパティ `settings` の直下にネストされたオブジェクトです。これは、UI に表示される複数の色固有の設定を、構成するために使用されます。

<!-- 
Take a look at the `color` property in the context of a `theme.json` file with its default values:
 -->

`theme.json` ファイルのコンテキストにおける、`color` プロパティとそのデフォルト値をみてみましょう:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"background": true,
			"custom": true,
			"customDuotone": true,
			"customGradient": true,
			"defaultDuotone": true,
			"defaultGradients": true,
			"defaultPalette": true,
			"duotone": [],
			"gradients": [],
			"link": true,
			"palette": [],
			"text": true
		}
	}
}
```

<!-- 
As you can see, most of the settings accept a boolean value, meaning that you can set them to either `true` or `false`. Others, like `duotone`, `gradients`, and `palette` take an array of values. These are the ones where you can register custom presets, and you will learn how to create them in this doc.
 -->

ご覧の通り、ほとんどの設定は真偽値を受け付けます。つまり、`true` または `false` のいずれかに設定できます。一方、`duotone`、`gradients`、`palette` などの設定は、値の配列を受け付けます。これらはカスタム・プリセットを登録できる設定であり、このドキュメントでその作成方法を学びます。

<!-- 
Color settings can largely be broken down into four groups that let you:
 -->

色の設定は主に4つのグループに分類でき、それぞれ以下の操作が可能です:

<!-- 
*   Enable or disable settings in the UI.
*   Enable or disable user customizations of colors, duotones filters, and gradients.
*   Enable or disable the core WordPress color, duotone, and gradient presets.
*   Register custom color, duotone, and gradient presets.
 -->

*   UI 内の設定の、有効化または無効化。
*   ユーザーによるカスタマイズの、色、デュオトーン・フィルター、グラデーションの、有効化または無効化。
*   WordPress コアのプリセットの、色、デュオトーン、グラデーションの、有効化または無効化。
*   カスタム・プリセットの、色、デュオトーン、グラデーションの、登録。

<!-- 
In the following sections, you will learn how each of these work.
 -->

以降のセクションでは、これらそれぞれのしくみについて学びます。

<!-- 
## Text, background, and link settings
 -->

## テキスト、背景、リンクの設定

<!-- 
In the block editor, you will often see **Text**, **Background**, and **Link** settings under the **Color** panel for a block, at least for those blocks that opt into support of one or more of them. 
 -->

ブロック・エディターでは、少なくともそれらの設定のいずれかをサポートするブロックについては、**色** パネルの下に **テキスト**、**背景**、**リンク** の設定が表示されることがよくあります。

<!-- 
These options appear like this in the interface:
 -->

これらのオプションは、インターフェース上で、次のように表示されます:

<!-- 
[![WordPress post editor with a Paragraph block that has a blue background. On the right, the Background color picker is open, revealing various color options.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-color-options.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-color-options.jpg?ssl=1)
 -->

[![青い背景の「段落」ブロックが配置された WordPress 投稿エディター。右側には背景色ピッカーが開いており、さまざまな色の選択肢が表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-color-options.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-color-options.jpg?ssl=1)

<!-- 
But just because a block registers support for text, background, and link colors doesn’t mean that your theme must also support them. That’s entirely up to you.
 -->

ただし、ブロックがテキスト色、背景色、リンク色の登録をサポートしているからといって、あなたのテーマもそれらをサポートしなければならないわけではありません。それは完全にあなた次第です。

<!-- 
WordPress lets you decide whether your theme supports any or all of the settings by defining the `background`, `link`, and `text` properties under `settings.color` in `theme.json`:
 -->

WordPress では、`theme.json` 内の `settings.color` 配下に `background`、`link`、`text` プロパティを定義することで、あなたのテーマがこれらの設定のいずれかまたはすべてをサポートするかどうかを決定できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"background": true,
			"link": true,
			"text": true
		}
	}
}
```

<!-- 
By default, all are set to `true`, so their associated controls will appear in the block interface. If you want to disable a feature, you only need to set its value to `false` in your `theme.json`.
 -->

デフォルトでは、すべてが `true` に設定されているため、関連するコントロールがブロック・インターフェースに表示されます。機能を無効化したい場合は、あなたの `theme.json` 内でその値を `false` に設定するだけで済みます。

<!-- 
For an exercise, try disabling the background color but still allow text and link colors:
 -->

練習として、背景色を無効にしつつ、テキストとリンクの色は有効にしたままにしてみましょう:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"background": false,
			"link": true,
			"text": true
		}
	}
}
```

<!-- 
Some core WordPress blocks and third-party blocks may have other color options that users can configure. These cannot be enabled or disabled via `theme.json` since they are not a standard component of the color system.
 -->

一部のコア WordPress ブロックやサードパーティ製ブロックには、ユーザーが設定可能な追加の色オプションが存在する場合があります。これらは色システムの標準コンポーネントではないため、`theme.json` 経由で有効化または無効化できません。

<!-- 
## Enabling and disabling user customizations
 -->

## ユーザーのカスタマイズ設定の有効化と無効化

<!-- 
One of the major decisions that you will need  to make for your theme is whether you want to allow users to create custom colors. On the one hand, enabling custom colors gives users a ton of flexibility and freedom to truly make their site their own. But maybe you’ve put in a lot of work getting the color scheme *just right* and want to make sure the user is only picking colors from a predetermined palette.
 -->

あなたのテーマで下す必要がある主要な決定事項の一つは、ユーザーがカスタム・カラーを作成できるようにするかどうかです。一方で、カスタム・カラーを有効にすると、ユーザーが自身のサイトを真に自分らしくカスタマイズするための柔軟性と自由度が、大幅に向上します。しかし、カラー配色を *完璧に* 調整するために多大な労力を費やした場合、ユーザーが事前に設定されたパレットからしか色を選べないようにしたいと思うかもしれません。

<!-- 
This may change depending on whether you are building a publicly-distributed theme vs. one for a client. Each project is unique, and you get to be the judge on what’s best for your design.
 -->

あなたが公開配布用のテーマを構築しているのか、クライアント向けのテーマを構築しているのかによって、この点は変わる可能性があります。各プロジェクトは独自のものであり、あなたのデザインにとって何が最適かについては、あなたが判断を下すことになります。

<!-- 
WordPress currently allows user-customized colors for three different features, which you can enable or disable via `theme.json`:
 -->

WordPress では現在、3つの異なる機能についてユーザーがカスタマイズ可能な色を設定でき、これらは `theme.json` を介して有効化または無効化できます:

<!-- 
*   **`custom`:** Whether the user can create and use custom colors.
*   **`customDuotone`:** Whether the user can create custom duotone filters (typically used for overlays on blocks with images).
*   **`customGradient`:** Whether the user can create custom background gradients.
 -->

*   **`custom`:** ユーザーが、カスタム・カラーを作成・使用できるかどうか。
*   **`customDuotone`:** ユーザーが、(主に画像付きブロックのオーバーレイに使用される) カスタム・デュオトーン・フィルターを作成できるかどうか。
*   **`customGradient`:** ユーザーが、カスタム背景グラデーションを作成できるかどうか。

<!-- 
By default, each of these features are enabled in `theme.json`:
 -->

デフォルトでは、これらの機能はそれぞれ `theme.json` で有効になっています:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"custom": true,
			"customDuotone": true,
			"customGradient": true
		}
	}
}
```

<!-- 
### User-customized colors
 -->

### ユーザーがカスタマイズした、色

<!-- 
When the `settings.colors.custom` value is set to `true` (the default), users will be able to define custom colors for individual blocks, as shown here:
 -->

`settings.colors.custom` の値が `true` (デフォルト) に設定されている場合、以下に示されるように、ユーザーは個々のブロックに対してカスタム・カラーを定義できます:

<!-- 
[![WordPress post editor with a Paragraph block in the editor with a blue background. The Text color option is open and shows a user selecting a custom color.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-colors.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-colors.jpg?ssl=1)
 -->

[![青い背景の「段落」ブロックが表示された、WordPress 投稿エディター。「テキスト」カラーオプションが表示され、ユーザーがカスタム・カラーを選択している様子。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-colors.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-colors.jpg?ssl=1)

<!-- 
Because this is enabled by default, try turning it off by setting the property to `false` in your `theme.json` file:
 -->

デフォルトで有効になっているため、あなたの `theme.json` ファイルでプロパティを `false` に設定して、オフにしてみましょう:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"custom": false
		}
	}
}
```

<!-- 
Now users will only be able to select from preset colors.
 -->

今後は、ユーザーはプリセット・カラーからしか選択できなくなります。

<!-- 
### User-customized duotone filters
 -->

### ユーザーがカスタマイズした、デュオトーン・フィルター

<!-- 
Duotone filters are generally supported by blocks that display an image. The filter is applied as an overlay above the image, creating a duotone effect. The two-color filter allows users to select a shadow and highlight color.
 -->

デュオトーン・フィルターは、一般的に画像を表示するブロックでサポートされています。フィルターは画像の上にオーバーレイとして適用され、デュオトーン効果を生み出します。この2色フィルターでは、ユーザーがシャドウ色とハイライト色を選択できます。

<!-- 
By default, users can create custom duotone filters as shown here:
 -->

デフォルトでは、以下に示されるように、ユーザーはカスタム・デュオトーン・フィルターを作成できます:

<!-- 
[![WordPress post editor showing an Image block with the custom duotone filters option open.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-duotone-scaled.jpg?resize=2560%2C1333&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-duotone-scaled.jpg?ssl=1)
 -->

[![カスタム・デュオトーン・フィルター・オプションが開いている「画像」ブロックを表示する、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-duotone-scaled.jpg?resize=2560%2C1333&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-duotone-scaled.jpg?ssl=1)

<!-- 
Since custom duotone filters are enabled by default, you must set the `settings.color.customDuotone` property to `false` if you do not want to allow users to add custom colors:
 -->

カスタム・デュオトーン・フィルターはデフォルトで有効になっているため、ユーザーがカスタム・カラーを追加できないようにするには、`settings.color.customDuotone` プロパティを `false` に設定する必要があります:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"customDuotone": false
		}
	}
}
```

<!-- 
### User-customized gradients
 -->

### ユーザーがカスタマイズした、グラデーション

<!-- 
Like most other color settings, custom gradients are enabled by default. This allows your theme users to define a gradient background for any block that supports it as shown here:
 -->

他のほとんどの色の設定と同様に、カスタム・グラデーションはデフォルトで有効になっています。これにより、以下に示されるように、あなたのテーマ・ユーザーはグラデーション背景をサポートする任意のブロックに対して、グラデーション背景を定義できます:

<!-- 
[![WordPress post editor with a Cover block shown. In the right sidebar, the gradient picker is open for the Overlay option.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-gradients.jpg?ssl=1)
 -->

[![「カバー」ブロックが表示された、WordPress 投稿エディター。右サイドバーには、「オーバーレイ」オプション用のグラデーション・ピッカーが開いている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-json-custom-gradients.jpg?ssl=1)

<!-- 
If you’ve carefully fine-tuned the gradients you want available to the user or simply want to disable custom gradients altogether, you can turn this feature off by setting `settings.color.customGradient` to `false` in `theme.json`:
 -->

ユーザーが利用できるグラデーションを慎重に調整した場合、またはカスタム・グラデーションを完全に無効化したい場合は、`theme.json` 内で `settings.color.customGradient` を `false` に設定することで、この機能をオフにできます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"customGradient": false
		}
	}
}
```

<!-- 
## Default WordPress presets
 -->

## デフォルトの WordPress プリセット

<!-- 
WordPress creates its own presets for each of the color features. As is the case with user-defined colors, you will need to decide whether you want to give users access to these. They will often clash with your theme’s color palette, but you may also opt to give users complete freedom to decide on their own.
 -->

WordPress はそれぞれの色の機能ごとに、独自のプリセットを作成します。ユーザー定義の色と同様に、これらのプリセットをユーザーに利用させるかどうかを、決定する必要があります。これらはあなたのテーマのカラーパレットと衝突することが多いですが、ユーザーに完全に自由に決めさせることも選択できます。

<!-- 
WordPress currently allows user-customized colors for three different features, which you can enable or disable via `theme.json`:
 -->

WordPress では現在、3つの異なる機能についてユーザーがカスタマイズ可能な色を設定でき、これらは `theme.json` を介して有効化または無効化できます:

<!-- 
*   `**defaultDuotone**`: Whether the user can select from WordPress’ default duotone filter presets (typically used for overlays on blocks with images).
*   **`defaultGradients`:** Whether the user can select from WordPress’ default background gradient presets.
*   **`defaultPalette`:** Whether the user can select colors from WordPress’ default color palette.
 -->

*   **`defaultDuotone`**: ユーザーが、WordPress デフォルトの、(主に画像付きブロックのオーバーレイに使用される) デュオトーン・フィルター・プリセットから選択できるかどうか。
*   **`defaultGradients`:** ユーザーが、WordPress デフォルトの、背景グラデーション・プリセットから選択できるかどうか。
*   **`defaultPalette`:** ユーザーが、WordPress デフォルトの、カラーパレットから色を選択できるかどうか。

<!-- 
By default, each of these features are enabled in `theme.json`:
 -->

デフォルトでは、これらの機能はそれぞれ `theme.json` で有効になっています:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"defaultDuotone": true,
			"defaultGradients": true,
			"defaultPalette": true
		}
	}
}
```

<!-- 
It’s important to note that, even if these settings are disabled, WordPress will still generate the CSS custom properties for its presets. This is for backward-compatibility and so that users do not lose colors, gradients, or duotone filters that they have previously chosen when using another theme.
 -->

これらの設定が無効化されていても、WordPress はプリセット用の CSS カスタム・プロパティを生成し続ける点に注意が必要です。これは下位互換性を確保し、ユーザーが以前に別のテーマで使用した際に選択したカラー、グラデーション、デュオトーン・フィルターを失わないようにするためです。

<!-- 
### Default color palette
 -->

### デフォルトのカラーパレット

<!-- 
WordPress ships with its own color palette, which is enabled by default for themes that have not opted out of it. It contains the following colors:
 -->

WordPress には独自のカラーパレットが同梱されており、これを無効化していないテーマではデフォルトで有効になります。以下の色が含まれています:

<!-- 
*   Black
*   Cyan bluish gray
*   White
*   Pale pink
*   Vivid red
*   Luminous vivid orange
*   Luminous vivid amber
*   Light green cyan
*   Vivid green cyan
*   Pale cyan blue
*   Vivid cyan blue
*   Vivid purple
 -->

*   黒色
*   青みがかった灰青色
*   白色
*   淡いピンク色
*   鮮やかな赤色
*   ごく鮮やかなオレンジ色
*   ごく鮮やかな琥珀色
*   薄い青緑色
*   鮮やかな、青緑色
*   淡い、緑がかった青
*   鮮やかな、緑がかった青
*   鮮やかな紫色

<!-- 
Color presets are available for the **Text**, **Background**, **Link**, and potentially other color controls as shown in this screenshot:
 -->

**テキスト**、**背景**、**リンク**、およびその他の色の設定に対して、このスクリーンショットに示すようにカラー・プリセットが利用可能です:

<!-- 
[![WordPress post editor with a Group block wrapping a Paragraph. The Text color option is highlighted in the right sidebar.](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-colors.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-colors.jpg?ssl=1)
 -->

[![「段落」を囲む「グループ」ブロックが表示された、WordPress 投稿エディター。右サイドバーに「テキスト」カラーオプションが強調表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-colors.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-colors.jpg?ssl=1)

<!-- 
There are times when you might want to disable the core WordPress colors, and you can do so by setting `settings.color.defaultPalette` to `false` in `theme.json`:
 -->

WordPress のコアカラーを無効にしたい場合は、`theme.json` 内で `settings.color.defaultPalette` を `false` に設定することで実現できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"defaultPalette": false
		}
	}
}
```

<!-- 
### Default duotone filters
 -->

### デフォルトのデュオトーン・フィルター

<!-- 
WordPress has several default duotone filter presets that it defines:
 -->

WordPress は、定義済みのデフォルトのデュオトーン・フィルター・プリセットをいくつか備えています:

<!-- 
*   Dark Grayscale
*   Grayscale
*   Purple and yellow
*   Blue and red
*   Midnight
*   Magenta and yellow
*   Purple and green
*   Blue and orange
 -->

*   暗いグレースケール
*   グレースケール
*   紫色と黄色
*   青色と赤色
*   ごく暗い、紫みの青色
*   赤紫色と黄色
*   紫色と緑色
*   青色とオレンジ色

<!-- 
These will appear for blocks that support duotone filters (generally used as an overlay for blocks with images), as shown here:
 -->

これらは、以下に示されるように、(通常、画像付きブロックのオーバーレイに使用される) デュオトーン・フィルターをサポートするブロックに表示されます:

<!-- 
[![WordPress post editor with a purple and yellow duotone filter applied to an Image in the content canvas.](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-duotone-filters.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-duotone-filters.jpg?ssl=1)
 -->

[![コンテンツ・キャンバス内の「画像」に対して、紫と黄色のデュオトーン・フィルターを適用した、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-duotone-filters.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-duotone-filters.jpg?ssl=1)

<!-- 
If you do not want to allow your theme users to select from the default duotone presets, you must set `settings.color.defaultDuotone` to `false` in `theme.json`:
 -->

あなたのテーマユーザーが、デフォルトのデュオトーン・プリセットから選択できるようにしたくない場合、`theme.json` 内で `settings.color.defaultDuotone` を `false` に設定する必要があります:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"defaultDuotone": false
		}
	}
}
```

<!-- 
### Default gradients
 -->

### デフォルトのグラデーション

<!-- 
By default, WordPress defines several gradients for users to pick and choose from. These can be added to blocks that support gradient backgrounds:
 -->

デフォルトで、WordPress はユーザーが選択できる、複数のグラデーションを定義しています。これらはグラデーション背景をサポートするブロックに、追加できます:

<!-- 
*   Vivid cyan blue to vivid purple
*   Light green cyan to vivid green cyan
*   Luminous vivid amber to luminous vivid orange
*   Luminous vivid orange to vivid red
*   Very light gray to cyan bluish gray
*   Cool to warm spectrum
*   Blush light purple
*   Blush bordeaux
*   Luminous dusk
*   Pale ocean
*   Electric grass
*   Midnight
 -->

*   鮮やかな、緑がかった青から鮮やかな紫色
*   薄い青緑色から鮮やかな、青緑色
*   ごく鮮やかな琥珀色からごく鮮やかなオレンジ色
*   ごく鮮やかなオレンジ色から鮮やかな赤色
*   最も明るい灰色から青みがかった灰青色
*   寒色から暖色のスペクトラム範囲
*   血色感のある、淡い紫色
*   血色感のある、ボルドー色
*   ごく鮮やかな、夕暮れ色
*   淡い、青色
*   光沢感のある、草色
*   ごく暗い、紫みの青色

<!-- 
They appear as shown here in the **Background > Gradient** control in the user interface:
 -->

これらは UI の **背景 > グラデーション** コントロールに以下のように表示されます:

<!-- 
[![WordPress post editor with a Group block and a purple and orange background gradient selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-gradients.jpg?ssl=1)
 -->

[![紫とオレンジの背景グラデーションが適用された「グループ」ブロックが表示された、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/default-gradients.jpg?ssl=1)

<!-- 
The core WordPress gradient presets are enabled by default, but there are times when you may want to disable them for your theme. You can do so by setting `settings.color.defaultGradients` to `false` in your `theme.json`:
 -->

WordPress のコア・グラデーション・プリセットはデフォルトで有効化されているが、あなたのテーマでは無効化したい場合もあるでしょう。あなたの `theme.json` 内で `settings.color.defaultGradients` を `false` に設定することで無効化できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"defaultGradients": false
		}
	}
}
```

<!-- 
## Registering custom color presets
 -->

## カスタム・カラープリセットの登録

<!-- 
Just like WordPress defines its own color, duotone, and gradient presets, so can you. This is a powerful feature that allows you to customize how your theme looks on the front end of the site and which colors your theme users can select from in the block editor.
 -->

WordPress が独自の色、デュオトーン、グラデーションのプリセットを定義するように、あなたも同様に定義できます。これは強力な機能であり、サイトのフロントエンドにおける、あなたのテーマの外観をカスタマイズし、ブロック・エディター内であなたのテーマユーザーが選択できる色を指定することを可能にします。

<!-- 
You can set presets for three different features via `theme.json`:
 -->

`theme.json` を通じて、3つの異なる機能のプリセットを設定できます:

<!-- 
*   `**duotone**`: An array of duotone filters that a user can choose from (typically used for overlays on blocks with images).
*   `**gradients**`: An array of background gradient objects that a user can choose from.
*   **`palette`:** An array of color objects that a user can choose from.
 -->

*   **`duotone`**: ユーザーが選択可能な、(主に画像付きブロックのオーバーレイに使用される) デュオトーン・フィルターの配列。
*   **`gradients`**: ユーザーが選択可能な、背景グラデーション・オブジェクトの配列。
*   **`palette`:** ユーザーが選択可能な、色オブジェクトの配列。

<!-- 
Here is what this would look like in `theme.json` (note that there are no presets yet registered):
 -->

以下が `theme.json` での実装例です (なお、まだプリセットは登録されていません):

```json
{
	"version": 2,
	"settings": {
		"color": {
			"duotone": [],
			"gradients": [],
			"palette": []
		}
	}
}
```

<!-- 
WordPress will automatically generate CSS custom properties for each of your presets in the form of `--wp--preset--{type}--{slug}`. So a color palette preset with the slug of `contrast` will become `--wp--preset--color--contrast`. 
 -->

WordPress は、あなたのプリセットごとに `--wp--preset--{type}--{slug}` という形式で CSS カスタム・プロパティを自動生成します。したがって、スラッグが `contrast` のカラーパレット・プリセットは `--wp--preset--color--contrast` になります。

<!-- 
You can access these in your `theme.json` styles via the CSS custom property itself or through a special naming convention of `var:preset|{type}|{slug}`. You will learn more about this in the `theme.json` [Styles documentation](https://docs.google.com/document/d/1jFI5wPr3cjaac4xDaH7OIwc5QqDo1OAGNHt23zR7Sb4/edit#).
 -->

これらのプリセットは、`theme.json` のスタイル内で CSS カスタム・プロパティ自体を通じて、または `var:preset|{type}|{slug}` という特別な命名規則を用いてアクセスできます。これについての詳細は、`theme.json` [スタイル・ドキュメント](https://docs.google.com/document/d/1jFI5wPr3cjaac4xDaH7OIwc5QqDo1OAGNHt23zR7Sb4/edit#) で学ぶことができます。

<!-- 
WordPress will also sometimes generate CSS classes based on the preset. For example, the `contrast` color palette preset will have an associated class for `.has-contrast-color` when used as a block’s text color and `.has-contrast-background-color` when used as a background.
 -->

WordPress はプリセットにもとづいて CSS クラスを生成することもあります。たとえば、`contrast` カラーパレット・プリセットでは、ブロックのテキスト色として使用すると `.has-contrast-color` の関連クラスが、背景色として使用すると `.has-contrast-background-color` の関連クラスが割り当てられます。

<!-- 
### Custom color palette
 -->

### カスタム・カラーパレット

<!-- 
When building a theme you will almost always want to register your own color palette. For some themes, this may be as simple as a couple of colors. Others could potentially include dozens of colors.
 -->

テーマを構築する際には、ほぼ必ず独自のカラーパレットを登録することになります。テーマによっては、数色だけというシンプルな場合もあります。一方で、数十色もの色を含む可能性のある場合も考えられます。

<!-- 
In the end, it’s your theme, and WordPress gives you the tools to build your design.
 -->

結局のところ、それはあなたのテーマであり、WordPress はあなたのデザインを構築するためのツールを提供するのです。

<!-- 
You can register custom colors via the `settings.color.palette` property in `theme.json`:
 -->

カスタム・カラーは、`theme.json` 内の `settings.color.palette` プロパティで登録できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"palette": []
		}
	}
}
```

<!-- 
The `palette` property accepts an array of color objects, and each of those objects has three properties that you must set:
 -->

`palette` プロパティは、色オブジェクトの配列を受け付け、それらの各オブジェクトには、設定が必要な3つのプロパティがあります:

<!-- 
*   `**color**`: A valid CSS color value.
*   **`name`:** The label for your color, which will be internationalized (so that it can be translated) and shown to the user in some contexts, such as tooltips.
*   **`slug`:** A unique machine-readable slug/ID for your color. This is used to generate CSS custom properties and CSS classes.
 -->

*   **`color`**: 有効な CSS カラー値。
*   **`name`:** 国際化 (翻訳可能) され、ツールチップなどのコンテキストでユーザーに表示される、あなたの色のラベル。
*   **`slug`:** CSS カスタム・プロパティと CSS クラスを生成するために使用される、あなたの色専用のユニークな機械可読スラグ/ID。

<!-- 
Suppose you wanted to register three colors named Base, Contrast, and Primary for your theme. They would appear in the color picker like so:
 -->

あなたのテーマ用に、Base、Contrast、Primary という名前の3色を登録したいとしましょう。それらはカラーピッカーに、次のように表示されます:

<!-- 
[![WordPress post editor showing a Group block around a Paragraph. The Group has a thick blue border and black text selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-color-palette.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-color-palette.jpg?ssl=1)
 -->

[![「段落」の周りに「グループ」ブロックを表示している、WordPress 投稿エディター。「グループ」には太い青色の枠線と、選択された黒色のテキストが設定されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-color-palette.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-color-palette.jpg?ssl=1)

<!-- 
For your custom colors to appear in the interface, you must add them to the `settings.color.palette` array as shown in this code snippet:
 -->

あなたのカスタム・カラーをインターフェースに表示させるには、このコード・スニペットに示すように、`settings.color.palette` 配列に追加する必要があります:

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
					"color": "#89CFF0",
					"name": "Primary",
					"slug": "primary"
				}
			]
		}
	}
}
```

<!-- 
You can add as few or as many colors as you want, and there are no official naming schemes.
 -->

好きなだけ色を追加できるし、公式の命名規則もありません。

<!-- 
Despite there not being an official naming scheme for colors, the `base` and `contrast` slugs are *de facto* standards [that were set forth](https://github.com/WordPress/Documentation-Issue-Tracker/issues/563) by the Twenty Twenty-Three default theme. It is recommended to use `base` for the site background and `contrast` for text. This provides the greatest future-proofing and compatibility between themes. It also gives plugin authors a standard set of fallback colors when needed.
 -->

色に対する公式の命名規則は存在しないものの、`base` と `contrast` のスラッグは、Twenty Twenty-Three デフォルト・テーマによって [定められた](https://github.com/WordPress/Documentation-Issue-Tracker/issues/563) *事実上の* 標準です。サイトの背景には `base` を、テキストには `contrast` を使用することを推奨します。これにより、将来のテーマ変更に対する耐性とテーマ間の互換性が最大限に確保されます。また、プラグイン開発者が必要な場合に利用できる、標準的なフォールバック色も提供されます。

<!-- 
### Custom gradients
 -->

### カスタム・グラデーション

<!-- 
Like colors, you can also register a custom set of gradient presets. And there are no limits on the number of gradients your theme can support, so go wild and have a bit of fun!
 -->

色と同様に、グラデーション・プリセットのカスタム・セットも登録できます。あなたのテーマがサポートできるグラデーションの数に制限はないので、思いっきり自由に楽しんでください !

<!-- 
You can register custom gradients via the `settings.color.gradients` property in `theme.json`:
 -->

カスタム・グラデーションは、`theme.json` 内の `settings.color.gradients` プロパティで登録できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"gradients": []
		}
	}
}
```

<!-- 
The `gradients` property accepts an array of gradient objects, and each of those objects has three properties that you must set:
 -->

`gradients` プロパティは、グラデーション・オブジェクトの配列を受け付け、それらの各オブジェクトには、設定が必要な3つのプロパティがあります:

<!-- 
*   **`gradient`:** A valid CSS background gradient value.
*   **`name`:** The label for your gradient, which will be internationalized (so that it can be translated) and shown to the user in some contexts, such as tooltips.
*   **`slug`:** A unique machine-readable slug/ID for your gradient. This is used to generate CSS custom properties and CSS classes.
 -->

*   **`gradient`:** 有効な CSS 背景グラデーション値。
*   **`name`:** 国際化 (翻訳可能) され、ツールチップなどのコンテキストでユーザーに表示される、あなたのグラデーションのラベル。
*   **`slug`:** CSS カスタム・プロパティと CSS クラスを生成するために使用される、あなたのグラデーションの一意な機械可読スラッグ/ID。

<!-- 
Let’s suppose you have a couple of gradients named Emerald and Fabled Sunset that you want to add for your theme as shown here:
 -->

たとえば、以下に示されるように、あなたのテーマに追加したい「エメラルド」と「伝説の夕焼け」という名前のグラデーションがいくつかあるとしましょう:

<!-- 
[![WordPress post editor with a Group block that has a Purple to Yellow gradient background.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-gradients.jpg?ssl=1)
 -->

[![紫色から黄色へのグラデーション背景を持つ「グループ」ブロックが表示された、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-gradients.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-gradients.jpg?ssl=1)

<!-- 
Add the following to your `theme.json` to register them:
 -->

以下の内容をあなたの `theme.json` に追加して、登録してください:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"gradients": [
				{
					"gradient": "linear-gradient(to right, #10b981, #64a30d)",
					"name": "Emerald",
					"slug": "emerald"
				},
				{
					"gradient": "linear-gradient(-225deg,#231557,#44107a 29%,#ff1361 67%,#fff800)",
					"name": "Fabled Sunset",
					"slug": "fabled-sunset"
				}
			]
		}
	}
}
```

<!-- 
### Custom duotone filters
 -->

### カスタム・デュオトーン・フィルター

<!-- 
Like colors and gradients, you can register any number of custom duotone filters for your theme. This will allow your users to apply customizations directly to Image and other blocks that support duotone.
 -->

色やグラデーションと同様に、あなたのテーマ用にいくつでもカスタム・デュオトーン・フィルターを登録できます。これにより、あなたのユーザーはデュオトーンをサポートする「画像」ブロックやその他のブロックに対して、直接カスタマイズを適用できます。

<!-- 
You can register custom gradients via the `settings.color.duotone` property in `theme.json`:
 -->

カスタム・グラデーションは、`theme.json` 内の `settings.color.duotone` プロパティで登録できます:

```json
{
	"version": 2,
	"settings": {
		"color": {
			"duotone": []
		}
	}
}
```

<!-- 
The `duotone` property accepts an array of duotone objects, and each of those objects has three properties that you must set:
 -->

`duotone` プロパティは、デュオトーン・オブジェクトの配列を受け付け、それらの各オブジェクトには、設定が必要な3つのプロパティがあります:

<!-- 
*   **`colors`:** An array containing two valid CSS color values.
*   **`name`:** The label for your duotone filter, which will be internationalized (so that it can be translated) and shown to the user in some contexts, such as tooltips.
*   **`slug`:** A unique machine-readable slug/ID for your duotone filter. This is used to generate CSS custom properties and CSS classes.
 -->

*   **`colors`:** 2つの有効な CSS カラー値を含む配列。
*   **`name`:** 国際化 (翻訳可能) され、ツールチップなどのコンテキストでユーザーに表示される、あなたのデュオトーン・フィルターのラベル。
*   **`slug`:** CSS カスタム・プロパティと CSS クラスの生成に使用される、あなたのデュオトーン・フィルターの一意なマシン可読スラッグ/ID。

<!-- 
Suppose you wanted to create to create two duotone filters—one for red shadows and highlights and a similar one for blues, as shown below:
 -->

たとえば、2つのデュオトーンフィルターを作成したい、としましょう — 以下に示すように、ひとつは赤色のシャドウとハイライト用、もうひとつは青色用の類似フィルターです:

<!-- 
[![WordPress post editor with a blue-tinted duotone filter applied to an Image block.](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-duotone-filters.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-duotone-filters.jpg?ssl=1)
 -->

[![「画像」ブロックに青みがかったデュオトーン・フィルターを適用した、WordPress 投稿エディター。](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-duotone-filters.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/theme-duotone-filters.jpg?ssl=1)

<!-- 
To register the Red and Blue dutone filters, add this code to your `theme.json`:
 -->

「赤色と青色」デュトーン・フィルターを登録するには、あなたの `theme.json` にこのコードを追加してください:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"color": {
			"duotone": [
				{
					"colors": [
						"#450a0a",
						"#fef2f2"
					],
					"name": "Red",
					"slug": "red"
				},
				{
					"colors": [
						"#172554",
						"#eff6ff"
					],
					"name": "Blue",
					"slug": "blue"
				}
			]
		}
	}
}
```

<!-- 
Duotone does not currently support CSS custom properties or references and cannot be dynamically generated. There is an [open ticket](https://github.com/WordPress/gutenberg/issues/33905) to solve this issue.
 -->

デュオトーンは現在、CSS カスタム・プロパティや参照をサポートしておらず、動的に生成できません。この課題を解決するための [オープン・チケット](https://github.com/WordPress/gutenberg/issues/33905) が存在します。