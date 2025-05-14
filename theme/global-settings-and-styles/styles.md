# Styles

The `styles` property in `theme.json` lets you configure settings at the global level, for individual elements, and individual blocks. WordPress supports a standard subset of the CSS specification, but also allows you to add custom CSS directly in your `theme.json` file.

When possible, it is recommended to add your theme styles via the `styles` property, at least for standard WordPress features. This makes it possible for users to customize them via **Appearance > Editor > Styles** without CSS specificity issues.

This document contains links for learning about the available style properties and how to apply styles to your theme via its `theme.json` file.

## The styles property

`styles` is a top-level property in `theme.json` and has multiple nested properties that you can define. And some of those nested properties have multiple levels of nesting of their own.

The following is an overarching look at these properties in the context of a `theme.json` file:

```json
{
	"version": 2,
	"styles": {
		"elements": {},
		"blocks": {}
	}
}
```

The following is an example of what the `styles` property could look like in a custom `theme.json` file. This should give you a feel for how it is structured, but you will dive into this more deeply as you read through this section of the handbook:

```json
{
	"version": 2,
	"styles": {
		"color": {
			"text": "#000000",
			"background": "#ffffff"
		},
		"elements": {
			"button": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		},
		"blocks": {
			"core/code": {
				"color": {
					"text": "#ffffff",
					"background": "#000000"
				}
			}
		}
	}
}
```

## Styles documentation

Use the following links to explore configuring styles via `theme.json` file:

*   **[Applying Styles](https://developer.wordpress.org/themes/global-settings-and-styles/styles/applying-styles/):** How to apply custom styles to your theme using the standard JSON syntax.
*   **[Using Presets](https://developer.wordpress.org/themes/global-settings-and-styles/styles/using-presets/):** How to use the presets that you’ve configured via the `settings` property in your styles.
*   **[Styles Reference](https://developer.wordpress.org/themes/global-settings-and-styles/styles/styles-reference/):** A reference guide for the available style properties that you can use in `theme.json`.