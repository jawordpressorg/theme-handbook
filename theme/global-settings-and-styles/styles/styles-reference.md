# Styles Reference

This is a reference to the available style properties that you can apply to the root element (global), individual elements, and individual blocks in `theme.json`. Please review the [Applying Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/) documentation to learn how to apply styles to your theme.

## Border

There are two methods for working with the `border` style property. The first is to target all sides of a block or element with the properties shown in the table:

| Property | Type | CSS Property |
| --- | --- | --- |
| `border.radius` | string, object | [`border-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-radius) |
| `border.color` | string, object | [`border-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-color) |
| `border.style` | string, object | [`border-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style) |
| `border.width` | string, object | [`border-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-width) |

Example usage in `theme.json`:

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

The second method is to specifically target the `top`, `right`, `bottom`, and `left` sides:

| Property | Type | CSS Property |
| --- | --- | --- |
| `border.<side>.color` | string, object | `border-<side>-color` |
| `border.<side>.style` | string, object | `border-<side>-style` |
| `border.<side>.width` | string, object | `border-<side>-width` |

Example usage in `theme.json`:

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

## Color

The `color` style property lets you define the default text, background, and link colors for a block or element:

| Property | Type | CSS Property |
| --- | --- | --- |
| `color.text` | string, object | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) |
| `color.background-color` | string, object | [`background-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color) |
| `color.link` | string, object | [`color`](https://developer.mozilla.org/en-US/docs/Web/CSS/color) (applied to nested `<a>` elements) |

Example usage in `theme.json`:

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

## Dimensions

The `dimensions` style property lets you define the minimum height for a block or element:

| Property | Type | CSS Property |
| --- | --- | --- |
| `dimensions.minHeight` | string, object | [`min-height`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-height) |

Example usage in `theme.json`:

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

## Filter

The `filter` style property lets you define filters for a block or element. Currently, you can set a default duotone filter:

| Property | Type | CSS Property |
| --- | --- | --- |
| `filter.duotone` | string, object | [`filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter) |

Example usage in `theme.json`:

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

## Shadow

The `shadow` style property lets you define the default box-shadow style for a block or element:

| Property | Type | CSS Property |
| --- | --- | --- |
| `shadow` | string, object | [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) |

Example usage in `theme.json`:

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

## Spacing

The `spacing` style property lets you define the default gap, margin, and padding for a block or element:

| Property | Type | CSS Property |
| --- | --- | --- |
| `blockGap` | string, object | [`margin-top`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin-top), [`gap`](https://developer.mozilla.org/en-US/docs/Web/CSS/gap) |
| `margin.<side>` | string, object | [`margin-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/margin) |
| `padding.<side>` | string, object | [`padding-<side>`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) |

You can define any or all of the sides (`top`, `right`, `bottom`, `left`) for the `margin` and `padding` style properties.

Example usage in `theme.json`:

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

## Typography

The `typography` style property lets you define default font and text-related styles for a block or element:

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

Example usage in `theme.json`:

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

## CSS

The `css` property lets you write custom CSS directly in `theme.json` for a block or element:

| Property | Type | CSS Property |
| --- | --- | --- |
| `css` | string | — |

Example usage in `theme.json`:

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

For an in-depth look at how to use the `css` style property, read [Per-block CSS with `theme.json`](https://developer.wordpress.org/news/2023/04/per-block-css-with-theme-json/) on the WordPress Developer Blog.