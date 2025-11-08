<!-- 
# Styles Reference
 -->

# スタイル・リファレンス

<!-- 
This is a reference to the available style properties that you can apply to the root element (global), individual elements, and individual blocks in `theme.json`. Please review the [Applying Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/) documentation to learn how to apply styles to your theme.
 -->

これは、`theme.json` 内でルート要素 (グローバル)、個々の要素、および個々のブロックに適用できる、利用可能なスタイル・プロパティのリファレンスです。あなたのテーマにスタイルを適用する方法については、[スタイルの適用](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/) ドキュメントをご覧ください。

<!-- 
## Border
 -->

## 枠線

<!-- 
There are two methods for working with the `border` style property. The first is to target all sides of a block or element with the properties shown in the table:
 -->

`border` スタイル・プロパティを扱うには、2つの方法があります。1つ目は、ブロックや要素の全辺を対象とする方法で、以下の表に示すプロパティを使用します:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `border.radius` | string, object | [`border-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-radius) |
| `border.color` | string, object | [`border-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-color) |
| `border.style` | string, object | [`border-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style) |
| `border.width` | string, object | [`border-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-width) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `border.radius` | 文字列、オブジェクト | [`border-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-radius) |
| `border.color` | 文字列、オブジェクト | [`border-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-color) |
| `border.style` | 文字列、オブジェクト | [`border-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style) |
| `border.width` | 文字列、オブジェクト | [`border-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-width) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"border": {
			"color": "#000000",
			"style": "solid",
			"width": "1px"
		}
	}
}
```

<!-- 
The second method is to specifically target the `top`, `right`, `bottom`, and `left` sides:
 -->

2つ目は、`top`、`right`、`bottom`、`left` の各辺を個別に指定する方法です:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `border.<side>.color` | string, object | `border-<side>-color` |
| `border.<side>.style` | string, object | `border-<side>-style` |
| `border.<side>.width` | string, object | `border-<side>-width` |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `border.<side>.color` | 文字列、オブジェクト | `border-<side>-color` |
| `border.<side>.style` | 文字列、オブジェクト | `border-<side>-style` |
| `border.<side>.width` | 文字列、オブジェクト | `border-<side>-width` |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"border": {
			"top": {
				"color": "#000000",
				"style": "solid",
				"width": "1px"
			}
		}
	}
}
```

<!-- 
## Color
 -->

## 色

<!-- 
The `color` style property lets you define the default text, background, and link colors for a block or element:
 -->

`color` スタイル・プロパティを使用すると、ブロックや要素に対して、デフォルトのテキスト色、背景色、リンク色を定義できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `color.text` | string, object | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) |
| `color.background-color` | string, object | [`background-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color) |
| `color.link` | string, object | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) (applied to nested `<a>` elements) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `color.text` | 文字列、オブジェクト | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) |
| `color.background-color` | 文字列、オブジェクト | [`background-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color) |
| `color.link` | 文字列、オブジェクト | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) (ネストされた `<a>` 要素に適用される) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/group": {
				"color": {
					"text": "#000000",
					"background": "#ffffff",
					"link": "#777777"
				}
			}
		}
	}
}
```

<!-- 
## Dimensions
 -->

## 寸法

<!-- 
The `dimensions` style property lets you define the minimum height for a block or element:
 -->

`dimensions` スタイル・プロパティを使用すると、ブロックや要素に対して、最小高を定義できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `dimensions.minHeight` | string, object | [`min-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-height) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `dimensions.minHeight` | 文字列、オブジェクト | [`min-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-height) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/cover": {
				"dimensions": {
					"minHeight": "50vh"
				}
			}
		}
	}
}
```

<!-- 
## Filter
 -->

## フィルター

<!-- 
The `filter` style property lets you define filters for a block or element. Currently, you can set a default duotone filter:
 -->

`filter` スタイル・プロパティを使用すると、ブロックや要素に対して、フィルターを定義できます。現在、デフォルトのデュオトーン・フィルターを設定できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `filter.duotone` | string, object | [`filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `filter.duotone` | 文字列、オブジェクト | [`filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/image": {
				"filter": {
					"duotone": "var(--wp--preset--duotone--default-filter)"
				}
			}
		}
	}
}
```

<!-- 
## Shadow
 -->

## 影

<!-- 
The `shadow` style property lets you define the default box-shadow style for a block or element:
 -->

`shadow` スタイル・プロパティを使用すると、ブロックや要素に対して、デフォルトのボックス・シャドウ・スタイルを定義できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `shadow` | string, object | [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `shadow` | 文字列、オブジェクト | [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/heading": {
				"shadow": "0 1px 2px 0 rgb(0 0 0 / 0.05)"
			}
		}
	}
}
```

<!-- 
## Spacing
 -->

## 間隔

<!-- 
The `spacing` style property lets you define the default gap, margin, and padding for a block or element:
 -->

`spacing` スタイル・プロパティを使用すると、ブロックや要素に対して、デフォルトの隙間、マージン、パディングを定義できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `blockGap` | string, object | [`margin-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-top), [`gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/gap) |
| `margin.<side>` | string, object | [`margin-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) |
| `padding.<side>` | string, object | [`padding-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `blockGap` | 文字列、オブジェクト | [`margin-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-top)、[`gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/gap) |
| `margin.<side>` | 文字列、オブジェクト | [`margin-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) |
| `padding.<side>` | 文字列、オブジェクト | [`padding-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) |

<!-- 
You can define any or all of the sides (`top`, `right`, `bottom`, `left`) for the `margin` and `padding` style properties.
 -->

`margin` および `padding` スタイル・プロパティでは、いずれかまたはすべての辺 (`top`、`right`、`bottom`、`left`) を定義できます。

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"spacing": {
			"blockGap": "2rem",
			"margin": {
				"top": "2rem",
				"bottom": "2rem"
			},
			"padding": {
				"left": "2rem",
				"right": "2rem"
			}
		}
	}
}
```

<!-- 
## Typography
 -->

## タイポグラフィ

<!-- 
The `typography` style property lets you define default font and text-related styles for a block or element:
 -->

`typography` スタイル・プロパティを使用すると、ブロックや要素に対して、デフォルトのフォントおよびテキスト関連のスタイルを定義できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `fontFamily` | string, object | [`font-family`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family) |
| `fontSize` | string, object | [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size) |
| `fontStyle` | string, object | [`font-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style) |
| `fontWeight` | string, object | [`font-weight`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight) |
| `letterSpacing` | string, object | [`letter-spacing`](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing) |
| `lineHeight` | string, object | [`line-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height) |
| `textColumns` | string | [`columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/columns) |
| `textDecoration` | string, object | [`text-decoration`](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) |
| `writingMode` | string, object | [`writing-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `fontFamily` | 文字列、オブジェクト | [`font-family`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family) |
| `fontSize` | 文字列、オブジェクト | [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size) |
| `fontStyle` | 文字列、オブジェクト | [`font-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style) |
| `fontWeight` | 文字列、オブジェクト | [`font-weight`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight) |
| `letterSpacing` | 文字列、オブジェクト | [`letter-spacing`](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing) |
| `lineHeight` | 文字列、オブジェクト | [`line-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height) |
| `textColumns` | 文字列 | [`columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/columns) |
| `textDecoration` | 文字列、オブジェクト | [`text-decoration`](https://developer.mozilla.org/en-US/docs/Web/CSS/text-decoration) |
| `writingMode` | 文字列、オブジェクト | [`writing-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/paragraph": {
				"typography": {
					"fontFamily": "Georgia, serif",
					"fontSize": "1.25rem",
					"fontStyle": "normal",
					"fontWeight": "500",
					"letterSpacing": "0",
					"lineHeight": "1.6",
					"textDecoration": "none"
				}
			}
		}
	}
}
```

<!-- 
## CSS
 -->

## CSS

<!-- 
The `css` property lets you write custom CSS directly in `theme.json` for a block or element:
 -->

`css` プロパティを使用すると、ブロックや要素に対して、カスタム CSS を `theme.json` に直接記述できます:

<!-- 
| Property | Type | CSS Property |
| --- | --- | --- |
| `css` | string | — |
 -->

| プロパティ | 型 | CSS プロパティ |
| --- | --- | --- |
| `css` | 文字列 | — |

<!-- 
Example usage in `theme.json`:
 -->

`theme.json` での使用例`:

```json
{
	"version": 2,
	"styles": {
		"blocks": {
			"core/gallery": {
				"css": "--wp--style--gallery-gap-default: 1rem;"
			}
		}
	}
}
```

<!-- 
For an in-depth look at how to use the `css` style property, read [Per-block CSS with `theme.json`](https://developer.wordpress.org/news/2023/04/per-block-css-with-theme-json/) on the WordPress Developer Blog.
 -->

`css` スタイル・プロパティの使用方法について詳しく知りたい場合は、WordPress 開発者ブログの [`theme.json` でのブロック単位の CSS](https://developer.wordpress.org/news/2023/04/per-block-css-with-theme-json/) をご覧ください。