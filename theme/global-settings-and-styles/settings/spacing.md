<!-- 
# Spacing
 -->

# 間隔

<!-- 
Spacing is one of the most complex parts of web design. It involves combining things like margin, padding, gap, line height, font size, and more into a harmonious flow. Doing this well requires a keen eye and a foundational understanding of how each of these pieces come together.
 -->

間隔調整は Web デザインにおいて最も複雑な要素の一つです。マージン、パディング、ギャップ、行間、フォント・サイズなどを調和のとれた流れに統合する作業を伴います。これを適切に行うには、鋭い観察眼と、これらの要素がどのように組み合わさるかについての基礎的な理解が必要です。

<!-- 
The `settings.spacing` property in `theme.json` covers settings related specifically to margin, padding, and gap.
 -->

`theme.json` 内の `settings.spacing` プロパティは、特にマージン、パディング、およびギャップに関連する設定を扱います。

<!-- 
This handbook also has documentation for [typography settings](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography) and [applying styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles) to blocks, both of which play roles in wrangling the spacing for your overall design.
 -->

本ハンドブックには [タイポグラフィの設定](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography) とブロックへの [スタイルの適用](https://developer.wordpress.org/themes/global-settings-and-styles/styles) に関するドキュメントも含まれており、どちらもあなたのデザイン全体の間隔を調整するうえで重要な役割を果たします。

<!-- 
## Spacing settings
 -->

## 間隔の設定

<!-- 
The `settings.spacing` object has several properties that you can configure:
 -->

`settings.spacing` オブジェクトには、設定可能なプロパティがいくつかあります:

<!-- 
*   **`blockGap`:** Whether to enable the **Block Spacing** option for blocks that support it. Can be a boolean value (`true`/`false`). Defaults to `null`. If set to null, WordPress’ generated CSS is also disabled.
*   **`margin`:**  Whether to enable the **Margin** option for supported blocks. Defaults to `false`.
*   **`padding`:** Whether to enable the **Padding** option for supported blocks. Defaults to `false`.
*   **`customSpacingSize`:** Whether to allow users to input custom spacing values for supported blocks. Defaults to `true`.
*   **`spacingScale`:** A configuration object for defining a custom spacing scale. WordPress defines a default scale with seven steps that increment by `1.5rem`.
*   **`spacingSizes`:** An array of custom size objects that may overrule the spacing scale or add to it.
*   **`units`:** An array of possible CSS units that users can select from when adding custom spacing.
 -->

*   **`blockGap`:** サポートされているブロックに対して、**ブロック間隔** オプションを有効化するか否かです。真偽値 (`true`/`false`) で指定できます。デフォルトは `null` です。null に設定すると、WordPress が生成する CSS も無効化されます。
*   **`margin`:** サポートされているブロックに対して、**マージン** オプションを有効にするか否かです。デフォルトは `false` です。
*   **`padding`:** サポートされているブロックに対して、**パディング** オプションを有効化するか否か。デフォルトは `false` です。
*   **`customSpacingSize`:** サポートされているブロックに対して、ユーザーがカスタム間隔値を入力できるようにするか否かです。デフォルトは `true` です。
*   **`spacingScale`:** カスタム間隔スケールを定義するための、設定オブジェクトです。WordPress はデフォルトで7段階のスケールを定義しており、各段階は `1.5rem` ずつ増加します。
*   **`spacingSizes`:** 間隔スケールを上書きしたり追加したりできるカスタム・サイズ・オブジェクトの配列です。
*   **`units`:** カスタム間隔を追加する際にユーザーが選択できる、利用可能な CSS 単位の配列です。

<!-- 
Here is what spacing settings look like the default WordPress `theme.json`:
 -->

以下は、WordPress のデフォルト `theme.json` における間隔設定の例です:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"blockGap": null,
			"customSpacingSize": true,
			"margin": false,
			"padding": false,
			"spacingScale": {
				"operator": "*",
				"increment": 1.5,
				"steps": 7,
				"mediumStep": 1.5,
				"unit": "rem"
			},
			"spacingSizes": [],
			"units": [ "px", "em", "rem", "vh", "vw", "%" ]
		}
	}
}
```

<!-- 
## Enabling or disabling spacing options
 -->

## 間隔オプションの有効化または無効化

<!-- 
As noted in the default settings in the previous section, there are several settings that are merely for enabling or disabling elements in the user interface. In this section, you will learn how to configure each of these.
 -->

前セクションのデフォルト設定で述べたように、UI の要素を有効化または無効化するだけの設定がいくつか存在します。本セクションでは、それらの各設定を構成する方法を学びます。

<!-- 
### Enabling block spacing (block gap)
 -->

### ブロック間隔 (ブロック・ギャップ) の有効化

<!-- 
In WordPress, the “block gap” refers to the spacing between blocks on a page. In most cases, this is the vertical spacing between blocks. But it can also refer to horizontal spacing when blocks are set in horizontal flex or in a grid layout.
 -->

WordPress では、「ブロック・ギャップ」とは、ページ上のブロック間の間隔を指します。ほとんどの場合、これはブロック間の垂直方向の間隔です。ただし、ブロックが水平方向のフレックス・レイアウトやグリッド・レイアウトでセットされている場合、水平方向の間隔を指すこともあります。

<!-- 
In flow layouts (the default), the block gap is applied using the CSS `margin-top` property to sibling elements. In flex or grid layouts, it is applied using the CSS `gap` property.
 -->

フロー・レイアウト (デフォルト) では、ブロック・ギャップは CSS の `margin-top` プロパティを使用して兄弟要素に適用されます。フレックス・レイアウトまたはグリッド・レイアウトでは、CSS の `gap` プロパティを使用して適用されます。

<!-- 
WordPress will automatically output the CSS for the block gap if this setting is not disabled entirely (the default). 
 -->

この設定が完全に無効化されていない場合 (デフォルト)、WordPress はブロック・ギャップ用の CSS を自動的に出力します。

<!-- 
You will learn more about defining block gap styles in the [Styles documentation](https://developer.wordpress.org/themes/global-settings-and-styles/styles), but having a baseline understanding of the terminology should help you decide how to work with this option.
 -->

ブロック・ギャップ・スタイルの定義については [スタイルのドキュメント](https://developer.wordpress.org/themes/global-settings-and-styles/styles) で詳しく学べますが、用語の基本的な理解があれば、このオプションの扱い方を決めるのに役立つでしょう。

<!-- 
The primary purpose of the `settings.spacing.blockGap` is to enable or disable the user interface for the **Block Spacing** control for blocks that support it. You can do this by setting it to `true` or `false`.
 -->

`settings.spacing.blockGap` の主な目的は、サポートされているブロックで **ブロック間隔** コントロールの UI を有効または無効にすることです。`true` または `false` に設定することで、これを実現できます。

<!-- 
However, you can also leave it as `null` (the default value). This disables the user interface. In addition, it removes the WordPress-generated block spacing CSS.
 -->

ただし、`null` (デフォルト値) のままにもできます。これにより UI が無効化されます。加えて、WordPress が生成するブロック間隔の CSS も削除されます。

<!-- 
Leaving this to the default `null` value is not usually recommended except in special cases. Generally, you would want consistent spacing as part of your design’s vertical rhythm. If set to `null`, you will need to handle that manually via custom CSS.
 -->

特別な場合を除き、デフォルトの `null` 値のままにしておくことは通常推奨されません。一般的に、デザインにおける垂直リズムの一部として、一貫した間隔を確保することが望ましいでしょう。`null` に設定した場合、カスタム CSS 経由で手動で処理する必要があります。

<!-- 
Use this table as a reference when determining which value to assign to `settings.spacing.blockGap`:
 -->

`settings.spacing.blockGap` に割り当てる値を決定する際の参考として、この表を使用してください:

<!-- 
| `blockGap` Value | Block Spacing Control | WordPress-generated CSS |
| --- | --- | --- |
| `null` | No | No |
| `true` | Yes | Yes |
| `false` | No | Yes |
 -->

| `blockGap` 値 | ブロック間隔の制御 | WordPress 生成の CSS |
| --- | --- | --- |
| `null` | No | No |
| `true` | Yes | Yes |
| `false` | No | Yes |

<!-- 
Now try configuring the setting. Open your `theme.json` file and set the property to `true`:
 -->

では設定を試してみましょう。`theme.json` ファイルを開き、プロパティを `true` にしましょう:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"blockGap": true
		}
	}
}
```

<!-- 
For blocks that support the property, you should now see the **Block Spacing** control appear. Here is a screenshot of what that looks like on the Post Template block:
 -->

プロパティをサポートするブロックでは、**ブロック間隔** コントロールが表示されるようになりました。以下のスクリーンショットは、「投稿テンプレート」ブロックでの表示例です:

<!-- 
[![WordPress editor with a Query Loop block. In the sidebar, the Block Spacing dropdown is open.](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-gap-post-template.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-gap-post-template.jpg?ssl=1)
 -->

[![「クエリー・ループ」ブロックが表示された WordPress エディター。サイドバーでは、「ブロック間隔」ドロップダウンが開いている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-gap-post-template.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/block-gap-post-template.jpg?ssl=1)

<!-- 
Because of the way the layout system works in WordPress, it will output CSS that is specific to individual containers to handle the gap between blocks nested within those containers. For the screenshot example, here’s what that CSS looks like:
 -->

WordPress のレイアウト・システムのしくみ上、個々のコンテナに固有の CSS を出力し、それらのコンテナ内にネストされたブロック間のギャップを処理します。スクリーンショットの例では、その CSS は以下のようになります:

```css
.wp-container-17.wp-container-17 > :first-child:first-child {
	margin-block-start: 0;
}
	
.wp-container-17.wp-container-17 > * {
	margin-block-start: var(--wp--preset--spacing--plus-4);
	margin-block-end: 0;
}
```

<!-- 
Of course, the ID (`17`) and value will be different on a case-by-case basis.
 -->

もちろん、ID (`17`) と値はケースごとに異なります。

<!-- 
### Enabling margin and padding
 -->

### マージンとパディングの有効化

<!-- 
The margin and padding settings are a little more straightforward. They are both disabled by default, and you can enable them by setting their values to `true` in `theme.json`:
 -->

マージンとパディングの設定は、もう少しわかりやすいです。どちらもデフォルトでは無効になっており、`theme.json` で値を `true` に設定することで有効にできます:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"margin": true,
			"padding": true
		}
	}
}
```

<!-- 
This will make the **Margin** and **Padding** controls appear for supported blocks in their inspector controls in the sidebar:
 -->

これにより、サイドバーのインスペクタ・コントロールで、サポートされているブロックに対して、**マージン** と **パディング** コントロールが表示されます:

<!-- 
[![WordPress editor with a Query Loop block. In the sidebar, the Margin dropdown is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/10/margin-padding-controls.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/margin-padding-controls.jpg?ssl=1)
 -->

[![「クエリー・ループ」ブロックが表示された、WordPress エディター。サイドバーでは、「マージン」ドロップダウンが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/margin-padding-controls.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/margin-padding-controls.jpg?ssl=1)

<!-- 
Of course, you are free to leave both of these to the default value of `false` or configure them to your liking.
 -->

もちろん、これら両方をデフォルト値の `false` のままにしておくことも、お好みに合わせて設定することも自由です。

<!-- 
### Disabling user-defined spacing sizes
 -->

### ユーザー定義間隔サイズの無効化

<!-- 
When any one of the `blockGap`, `margin`, or `padding` spacing settings are enabled, WordPress will output a user interface for setting those values for blocks that support them. By default, users can select from a list of preset spacing sizes (see “Spacing scale and sizes” below) or input a custom value.
 -->

`blockGap`、`margin`、または `padding` のいずれかの間隔設定が有効になっている場合、WordPress は、サポートされているブロックに対して、これらの値を設定するための UI を出力します。デフォルトでは、ユーザーはプリセットの間隔サイズの一覧 (「間隔スケールとサイズ」参照) から選択するか、カスタム値を入力できます。

<!-- 
In this screenshot, you can see that there is a custom **Block Spacing** setting chosen for the Buttons block:
 -->

このスクリーンショットでは、「ボタン」ブロックに対して、カスタム **ブロック間隔** 設定が選択されていることが確認できます:

<!-- 
[![Three buttons in the post editor. In the sidebar, the Block Spacing option is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/10/custom-spacing-size-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/custom-spacing-size-buttons.jpg?ssl=1)
 -->

[![投稿エディター内の3つのボタン。サイドバーでは、「ブロック間隔」オプションが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/custom-spacing-size-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/custom-spacing-size-buttons.jpg?ssl=1)

<!-- 
You may want to limit users to your predefined spacing scale or sizes for your theme. This is often a good idea if you want to ensure consistent spacing throughout your design.
 -->

あなたのテーマでは、定義済みの間隔スケールやサイズに、ユーザーを制限することをおすすめします。あなたのデザイン全体で一貫した間隔を確保したい場合、これはしばしば良いアイデアです。

<!-- 
To do this, you must set the `customSpacingSizes` setting to `false`. This disables the custom spacing option in the editor UI but leaves the control for the theme’s defined sizes available:
 -->

これを行うには、`customSpacingSizes` を `false` に設定する必要があります。これにより、エディター UI のカスタム間隔オプションは無効化されますが、テーマで定義されたサイズの制御は、有効なままとなります:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"customSpacingSize": false
		}
	}
}
```

<!-- 
With custom spacing sizes disabled, the **Block Spacing** option from the Buttons block example will be limited to the theme’s preset sizes:
 -->

カスタム間隔サイズが無効化されている場合、「ボタン」ブロックの例における **ブロック間隔** オプションは、テーマのプリセット・サイズに制限されます:

<!-- 
[![Three buttons in the post editor. In the sidebar, the Block Spacing dropdown is shown.](https://i0.wp.com/developer.wordpress.org/files/2023/10/preset-spacing-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/preset-spacing-buttons.jpg?ssl=1)
 -->

[![投稿エディター内の3つのボタン。サイドバーでは、「ブロック間隔」ドロップダウンが表示されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/preset-spacing-buttons.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/preset-spacing-buttons.jpg?ssl=1)

<!-- 
## Defining allowed spacing units
 -->

## 許可される間隔単位の定義

<!-- 
If you choose to enable the `settings.spacing.customSpaceSize` option covered in the previous section, you will need to make another choice: which CSS unit values will your theme allow?
 -->

前セクションで説明した `settings.spacing.customSpaceSize` オプションを有効にする場合、もう一つ選択する必要があります: あなたのテーマが許可する CSS 単位の値は ?

<!-- 
By default, WordPress lets users select from a subset of possible CSS units (there are dozens in the CSS specification). To choose which units you want to support, you must add them into the `settings.spacing.units` array in `theme.json` (shown with the defaults):
 -->

デフォルトでは、WordPress は、ユーザーが (CSS 仕様では数十種類も存在する) CSS 単位のサブセットから選択できるようにしています。サポートしたい単位を選択するには、`theme.json` 内の `settings.spacing.units` 配列にそれらを追加する必要があります (デフォルトは以下に示すとおり):

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"units": [ "px", "em", "rem", "vh", "vw", "%" ]
		}
	}
}
```

<!-- 
The currently-allowed possible units that you can choose from are:
 -->

現時点で選択可能な単位は、以下の通りです:

*   `px`
*   `%`
*   `em`
*   `rem`
*   `vw`
*   `vh`
*   `vmin`
*   `vmax`
*   `ch`
*   `ex`
*   `cm`
*   `mm`
*   `in`
*   `pc`
*   `pt`

<!-- 
As of WordPress 6.3, the allowed units are limited to the above list. There is an [open ticket](https://github.com/WordPress/gutenberg/issues/52441) to expand these to support more modern units.
 -->

WordPress 6.3時点では、許可される単位は上記のリストに限定されています。より現代的な単位をサポートするために、これらを拡張する [オープン・チケット](https://github.com/WordPress/gutenberg/issues/52441) が存在します。

<!-- 
## Spacing scale and sizes
 -->

## 間隔のスケールとサイズ

<!-- 
One of the most important things that you should configure in your `theme.json` file is your spacing presets. WordPress will generate these presets as CSS custom properties, loading them in the editor and front end.
 -->

`theme.json` ファイルで設定すべき、最も重要な事項の一つが、間隔プリセットです。WordPress はこれらのプリセットを CSS カスタム・プロパティとして生成し、エディターとフロントエンドでロードします。

<!-- 
Most designers will use some type of standard scaling system for handling spacing, and WordPress gives you the flexibility to use whatever system you choose.
 -->

ほとんどのデザイナーは、間隔処理に何らかの標準的なスケーリング・システムを使用し、WordPress では、あなたが選択したシステムを自由に使用できる、柔軟性が提供されています。

<!-- 
There are two methods for registering your spacing presets:
 -->

あなたの間隔プリセットを登録するには、次の2つの方法があります:

<!-- 
*   **`spacingScale`:** A generated scale based on your configuration values.
*   **`spacingSizes`:** Completely custom-defined spacing sizes.
 -->

*   **`spacingScale`:** あなたの設定値にもとづいて生成された、スケールです。
*   **`spacingSizes`:** 完全にカスタム定義された、間隔サイズです。

<!-- 
Technically, you can use both of these methods, mixing and matching them. But it is generally recommended to choose one over the other for simplicity.
 -->

技術的には、これらの方法を両方とも使用し、組み合わせて使うことも可能です。しかし、簡潔さを考慮すると、どちらか一方を選択することが一般的に推奨されます。

<!-- 
Spacing presets appear as choices for the **Block Spacing**, **Margin**, and **Padding** block controls (for blocks that support them). This means that you can present users with spacing options that are specific to your theme. You can also use these presets in the [Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles) section in your `theme.json` or custom CSS.
 -->

間隔プリセットは、(対応するブロックにおいて) **ブロック間隔**、**マージン**、**パディング** ブロック・コントロールの選択肢として表示されます。これにより、あなたのテーマ固有の間隔オプションをユーザーに提供できます。これらのプリセットは、あなたの `theme.json` の [スタイル](https://developer.wordpress.org/themes/global-settings-and-styles/styles) セクションやカスタム CSS でも使用できます。

<!-- 
WordPress generates a default spacing scale, as shown in this table:
 -->

WordPress は、以下の表に示すように、デフォルトの間隔スケールを生成します:

<!-- 
| CSS Custom Property | CSS Value | Label |
| --- | --- | --- |
| `--wp-preset--spacing--20` | `0.44rem` | 2X-Small |
| `--wp-preset--spacing--30` | `0.67rem` | X-Small |
| `--wp-preset--spacing--40` | `1rem` | Small |
| `--wp-preset--spacing--50` | `1.5rem` | Medium |
| `--wp-preset--spacing--60` | `2.25rem` | Large |
| `--wp-preset--spacing--70` | `3.38rem` | X-Large |
| `--wp-preset--spacing--80` | `5.06rem` | 2X-Large |
 -->

| CSS カスタム・プロパティ | CSS 値 | ラベル |
| --- | --- | --- |
| `--wp-preset--spacing--20` | `0.44rem` | XXS |
| `--wp-preset--spacing--30` | `0.67rem` | XS |
| `--wp-preset--spacing--40` | `1rem` | S |
| `--wp-preset--spacing--50` | `1.5rem` | M |
| `--wp-preset--spacing--60` | `2.25rem` | L |
| `--wp-preset--spacing--70` | `3.38rem` | XL |
| `--wp-preset--spacing--80` | `5.06rem` | XXL |

<!-- 
It is unlikely that this scale matches your design. So you will want to choose a method for overriding these default values.
 -->

このスケールがあなたのデザインに合う可能性は、低いでしょう。したがって、これらのデフォルト値を上書きする方法を検討する必要があります。

<!-- 
### Custom spacing scale
 -->

### カスタム間隔スケール

<!-- 
WordPress allows theme authors to create a custom spacing scale by providing a set of configuration instructions. Each step in the scale generates a custom CSS property with the slug of `--wp--preset--spacing--{step}` (steps appear in increments of 10, regardless of their value).
 -->

WordPress では、テーマ作者が設定指示のセットを提供することで、カスタム間隔スケールを作成できます。スケールの各ステップ (ステップは、値にかかわらず10刻みで表示される) は、`--wp--preset--spacing--{step}` のスラッグを持つカスタム CSS プロパティを生成します。

<!-- 
The `spacingScale` object has five sub-settings that themes can configure:
 -->

`spacingScale` オブジェクトには、テーマが設定可能な5つのサブ設定があります:

<!-- 
*   **`operator`:** The operator used to increment the scale. The available options are `+` (addition) and `*` (multiplication). The default value is `*`.
*   **`increment`:** A number in which to increment the scale by when used in conjunction with the `operator` setting. The default value is `1.5`.
*   **`steps`:** The total number of steps in the scale. The default value is `7`.
*   **`mediumStep`:** The medium value of the scale. The default value is `1.5`.
*   **`unit`:** A valid CSS spacing unit. The available options are `px`, `em`, `rem`, `vh`, `vw`, and `%`. The default value is `rem`.
 -->

*   **`operator`:** スケールを増加させる際に使用する演算子です。利用可能なオプションは `+` (加算) と `*` (乗算) です。デフォルト値は `*` です。
*   **`increment`:** `operator` 設定と組み合わせて使用する際、スケールを増加させる数値です。デフォルト値は `1.5` です。
*   **`steps`:** スケールの総ステップ数です。デフォルト値は `7` です。
*   **`mediumStep`:** スケールの中間値です。デフォルト値は `1.5` です。
*   **`unit`:** 有効な CSS 単位です。利用可能なオプションは `px`、`em`、`rem`、`vh`、`vw`、および `%` です。デフォルト値は `rem` です。

<!-- 
The following example is a custom scale with seven steps that increments by `0.25rem`:
 -->

以下の例では、7段階のカスタム・スケールを定義し、各ステップは `0.25rem` ずつ増加します:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"spacingScale": {
				"operator": "+",
				"increment": 0.25,
				"steps": 7,
				"mediumStep": 1,
				"unit": "rem"
			}
		}
	}
}
```

<!-- 
As shown in the screenshot, you should see a range slider the **Padding**, **Margin**, and **Block Spacing** controls for setting your registered values:
 -->

スクリーンショットに示されているように、あなたの登録値を設定するための **パディング**、**マージン**、および **ブロック間隔** のコントロールを備えた、範囲スライダーが表示されるはずです:

<!-- 
[![Stack block in the WordPress post editor. In the sidebar, various spacing options are adjusted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-scale.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-scale.jpg?ssl=1)
 -->

[![「縦積み」ブロックが表示されている、WordPress 投稿エディター。サイドバーでは、さまざまな間隔オプションが調整されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-scale.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-scale.jpg?ssl=1)

<!-- 
When there are seven or fewer spacing presets, the interface will show a range slider for spacing controls. But more than seven displays a dropdown select. This applies to both the `spacingScale` method used here and the `spacingSizes` method in the next section.
 -->

間隔プリセットが7つ以下の場合、インターフェースには間隔コントロール用の範囲スライダーが表示されます。ただし、7つを超えるとドロップダウンが表示されます。これは、ここで使用する `spacingScale` メソッドと、次セクションの `spacingSizes` メソッドの両方に適用されます。

<!-- 
This table represents your custom spacing scale (compare to the default scale to see how things have changed):
 -->

この表は、カスタム間隔スケールを表しています (デフォルトのスケールと比較して、どのように変化したかをご覧あれ):

<!-- 
| CSS Custom Property | CSS Value | Label |
| --- | --- | --- |
| `--wp-preset--spacing--20` | `0.25rem` | 2X-Small |
| `--wp-preset--spacing--30` | `0.5rem` | X-Small |
| `--wp-preset--spacing--40` | `0.75rem` | Small |
| `--wp-preset--spacing--50` | `1rem` | Medium |
| `--wp-preset--spacing--60` | `1.25rem` | Large |
| `--wp-preset--spacing--70` | `1.5rem` | X-Large |
| `--wp-preset--spacing--80` | `1.75rem` | 2X-Large |
 -->

| CSS カスタム・プロパティ | CSS 値 | ラベル |
| --- | --- | --- |
| `--wp-preset--spacing--20` | `0.25rem` | XXS |
| `--wp-preset--spacing--30` | `0.5rem` | XS |
| `--wp-preset--spacing--40` | `0.75rem` | S |
| `--wp-preset--spacing--50` | `1rem` | M |
| `--wp-preset--spacing--60` | `1.25rem` | L |
| `--wp-preset--spacing--70` | `1.5rem` | XL |
| `--wp-preset--spacing--80` | `1.75rem` | XXL |

<!-- 
The `mediumStep` value is always assigned to the `--wp--preset--spacing--50` preset when WordPress generates the CSS, and the other preset slugs in the scale extend up/down from this middle number in increments of 10. 
 -->

WordPress が CSS を生成する際、`mediumStep` 値は常に `--wp--preset--spacing--50` プリセットに割り当てられ、スケール内の他のプリセット・スラッグは、この中間値から10刻みで上下に広がっています。

<!-- 
The spacing scale will never go below `--wp--preset--spacing--10`. For scales with more than 10 steps, the bottom end of the scale will not generate presets because the `mediumStep` is always set to `--wp--preset--spacing--50`.
 -->

間隔スケールは `--wp--preset--spacing--10` を下回ることはありません。10ステップを超えるスケールの場合、`mediumStep` が常に `--wp--preset--spacing--50` に設定されるため、スケールの下限はプリセットを生成しません。

<!-- 
#### Disable the spacing scale
 -->

#### 間隔スケールの無効化

<!-- 
If you want to disable WordPress’ spacing scale altogether, you can set `steps` to `0` in `theme.json`:
 -->

WordPress の間隔スケーリングを完全に無効化したい場合は、`theme.json` で `steps` を `0` にセットできます:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"spacingScale": {
				"steps": 0
			}
		}
	}
}
```

<!-- 
This can be useful when choosing to register completely custom spacing sizes, as covered in the next section.
 -->

これは、次セクションで説明する、完全なカスタム間隔サイズの登録を選択する場合に有用です。

<!-- 
### Custom spacing sizes
 -->

### カスタム間隔サイズ

<!-- 
If you want more precise control over the spacing options, you can build out the individual spacing sizes instead of using the WordPress spacing scale system. This provides control over each option’s name, size, and slug.
 -->

より精密な間隔オプションのコントロールが必要な場合は、WordPress の間隔スケール・システムを使用する代わりに、個別の間隔サイズを設定できます。これにより、各オプションの名前、サイズ、スラッグをコントロールできます。

<!-- 
The `spacingSizes` property lets you define an array of size objects. Each size object accepts three values:
 -->

`spacingSizes` プロパティを使用すると、サイズ・オブジェクトの配列を定義できます。各サイズ・オブジェクトは、3つの値を受け付けます:

<!-- 
*   **`name`:** The human-readable title for the size, which can be translated.
*   **`size`:** A valid CSS size. This can be a number and unit, a fluid size using `clamp()`, or a reference to another custom CSS property.
*   **`slug` :** The slug for the size, which will be appended to a generated CSS custom property: `--wp--preset--spacing--{slug}`.
 -->

*   **`name`:** 翻訳可能で人間可読な、タイトルです。
*   **`size`:** 有効な CSS サイズです。数値と単位、`clamp()` を使用したフルード・サイズ、または別のカスタム CSS プロパティへの参照を指定できます。
*   **`slug` :** サイズのスラッグで、生成される CSS カスタム・プロパティの末尾に追加されます: `--wp--preset--spacing--{slug}`.

<!-- 
The following is an example of creating a five-step scale that increments by `0.25rem`:
 -->

以下は、`0.25rem` ずつ増加する5ステップのスケールを作成する例です:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"spacingSizes": [
				{
					"name": "Step 1",
					"size": "0.25rem",
					"slug": "10"
				},
				{
					"name": "Step 2",
					"size": "0.5rem",
					"slug": "20"
				},
				{
					"name": "Step 3",
					"size": "0.75rem",
					"slug": "30"
				},
				{
					"name": "Step 4",
					"size": "1rem",
					"slug": "40"
				},
				{
					"name": "Step 5",
					"size": "1.25rem",
					"slug": "50"
				}
			]
		}
	}
}
```

<!-- 
You should see a range slider the **Padding**, **Margin**, and **Block Spacing** controls for setting your registered values, as shown here:
 -->

あなたの登録値を設定するための **パディング**、**マージン**、**ブロック間隔** のコントロールが、以下のように範囲スライダーで表示されるはずです:

<!-- 
[![Stack block in the WordPress post editor. In the sidebar, various spacing options are adjusted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-sizes.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-sizes.jpg?ssl=1)
 -->

[![「縦積み」ブロックが表示されている、WordPress 投稿エディター。サイドバーでは、さまざまな間隔オプションが調整されている。](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-sizes.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/spacing-sizes.jpg?ssl=1)

<!-- 
This table represents your custom spacing sizes:
 -->

この表は、カスタム間隔サイズを表しています:

<!-- 
| CSS Custom Property | CSS Value | Label |
| --- | --- | --- |
| `--wp-preset--spacing--10` | `0.25rem` | Step 1 |
| `--wp-preset--spacing--20` | `0.5rem` | Step 2 |
| `--wp-preset--spacing--30` | `0.75rem` | Step 3 |
| `--wp-preset--spacing--40` | `1rem` | Step 4 |
| `--wp-preset--spacing--50` | `1.25rem` | Step 5 |
 -->

| CSS カスタム・プロパティ | CSS 値 | ラベル |
| --- | --- | --- |
| `--wp-preset--spacing--10` | `0.25rem` | ステップ1 |
| `--wp-preset--spacing--20` | `0.5rem` | ステップ2 |
| `--wp-preset--spacing--30` | `0.75rem` | ステップ3 |
| `--wp-preset--spacing--40` | `1rem` | ステップ4 |
| `--wp-preset--spacing--50` | `1.25rem` | ステップ5 |

<!-- 
#### Creating fluid sizes
 -->

#### フルード・サイズの作成

<!-- 
If you want to use fluid spacing, you must use the `settings.spacing.spacingSizes` method for controlling the size presets.
 -->

フルード・スペースを使用したい場合は、サイズ・プリセットをコントロールするために `settings.spacing.spacingSizes` メソッドを使用する必要があります。

<!-- 
To use fluid sizes, you merely need to add them as the `size` parameter for each of the size objects under `settings.spacing.spacingSizes`. `clamp()`, `min()`, `max()`, and other valid CSS values are supported.
 -->

フルード・サイズを適用するには、`settings.spacing.spacingSizes` 内の各サイズ・オブジェクトに対して、`size` パラメータとしてフルード・サイズを追加するだけです。`clamp()`、`min()`、`max()` などの有効な CSS 値がサポートされています。

<!-- 
Here is an example of a seven-step fluid spacing scale registered as individual sizes in `theme.json`:
 -->

以下は、`theme.json` に個別のサイズとして登録された、7ステップのフルード間隔スケーリングの例です:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"spacingSizes": [
				{
					"name": "Fluid Scale -3",
					"size": "clamp( 0.31rem, 0.11vw + 0.28rem,  0.35rem )",
					"slug": "minus-3"
				},
				{
					"name": "Fluid Scale -2",
					"size": "clamp( 0.47rem, 0.16vw + 0.42rem,  0.53rem )",
					"slug": "minus-2"
				},
				{
					"name": "Fluid Scale -1",
					"size": "clamp( 0.71rem, 0.25vw + 0.63rem,  0.79rem )",
					"slug": "minus-1"
				},
				{
					"name": "Fluid Scale +/- 0 (Base)",
					"size": "clamp( 1.06rem, 0.37vw + 0.95rem,  1.19rem )",
					"slug": "base"
				},
				{
					"name": "Fluid Scale +1",
					"size": "clamp( 1.20rem, 0.85vw + 0.94rem,  1.48rem )",
					"slug": "plus-1"
				},
				{
					"name": "Fluid Scale +2",
					"size": "clamp( 1.34rem, 1.5vw + 0.89rem,  1.86rem )",
					"slug": "plus-2"
				},
				{
					"name": "Fluid Scale +3",
					"size": "clamp( 1.86rem, 3.7vw + -0.05rem,  2.32rem )",
					"slug": "plus-3"
				}
			]
		}
	}
}
```

<!-- 
This results in the following values, as shown in this table:
 -->

この結果、この表に示される、以下の値が得られます:

<!-- 
| CSS Custom Property | CSS Value | Label |
| --- | --- | --- |
| `--wp-preset--spacing--minus-1` | `clamp( 0.31rem, 0.11vw + 0.28rem,  0.35rem )` | Fluid Scale -3 |
| `--wp-preset--spacing--minus-2` | `clamp( 0.47rem, 0.16vw + 0.42rem,  0.53rem )` | Fluid Scale -2 |
| `--wp-preset--spacing--minus-3` | `clamp( 0.71rem, 0.25vw + 0.63rem,  0.79rem )` | Fluid Scale -1 |
| `--wp-preset--spacing--base` | `clamp( 1.06rem, 0.37vw + 0.95rem,  1.19rem )` | Fluid Scale +/- 0 (Base) |
| `--wp-preset--spacing--plus-1` | `clamp( 1.20rem, 0.85vw + 0.94rem,  1.48rem )` | Fluid Scale +1 |
| `--wp-preset--spacing--plus-2` | `clamp( 1.34rem, 1.5vw + 0.89rem,  1.86rem )` | Fluid Scale +2 |
| `--wp-preset--spacing--plus-3` | `clamp( 1.86rem, 3.7vw + -0.05rem,  2.32rem )` | Fluid Scale +3 |
 -->

| CSS カスタム・プロパティ | CSS 値 | ラベル |
| --- | --- | --- |
| `--wp-preset--spacing--minus-1` | `clamp( 0.31rem, 0.11vw + 0.28rem,  0.35rem )` | フルード・スケール -3 |
| `--wp-preset--spacing--minus-2` | `clamp( 0.47rem, 0.16vw + 0.42rem,  0.53rem )` | フルード・スケール -2 |
| `--wp-preset--spacing--minus-3` | `clamp( 0.71rem, 0.25vw + 0.63rem,  0.79rem )` | フルード・スケール -1 |
| `--wp-preset--spacing--base` | `clamp( 1.06rem, 0.37vw + 0.95rem,  1.19rem )` | フルード・スケール ±0 (基準値) |
| `--wp-preset--spacing--plus-1` | `clamp( 1.20rem, 0.85vw + 0.94rem,  1.48rem )` | フルード・スケール +1 |
| `--wp-preset--spacing--plus-2` | `clamp( 1.34rem, 1.5vw + 0.89rem,  1.86rem )` | フルード・スケール +2 |
| `--wp-preset--spacing--plus-3` | `clamp( 1.86rem, 3.7vw + -0.05rem,  2.32rem )` | フルード・スケール +3 |