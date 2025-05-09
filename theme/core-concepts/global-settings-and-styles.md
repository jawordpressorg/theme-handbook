# Global Settings and Styles

As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), `theme.json` is a standard file that WordPress looks for in your theme. While it is not technically required for a block theme, it is almost always necessary to configure various settings and styles for your theme.

This documentation is a quick introduction on what `theme.json` is and how it works. However, it is such a massive topic that there is a dedicated chapter that explores everything you can do with it: [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/).

## What is theme.json?

`theme.json` is a configuration file that tells WordPress what settings you want to enable, how to style specific elements and blocks, and which templates and template parts to register.

Some of the things you can do with `theme.json` are:

*   Enable or disable features like drop caps, padding, margin, and line-height.
*   Add a color palette, gradients, duotones, and shadows.
*   Configure typographical features like font families, sizes, and more.
*   Add CSS custom properties.
*   Register custom templates and assign parts to template part areas.

Your `theme.json` configuration will be reflected in what you see in places like the post, template, and site editors in the WordPress admin. Custom styles, in particular, will be reflected in the **Styles** interface:

[![WordPress Site Editor viewing a Single Post template. On the right, the Buttons block is highlighted in the Styles interface.](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/global-styles-site-editor.jpg?ssl=1)

## theme.json structure

A `theme.json` file can be as little as a few lines of code, such as this example that enables the appearance tools for blocks:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {
		"appearanceTools": true
	}
}
```

Or it can be a massively complex file that spans 1,000s of lines of code. How many of the features you want to configure is entirely up to you.

The starting point is understanding the top-level properties that can be configured. Here is an outline of what this looks like:

```json
{
	"$schema": "https://schemas.wp.org/trunk/theme.json",
	"version": 2,
	"settings": {},
	"styles": {},
	"customTemplates": {},
	"templateParts": {},
	"patterns": []
}
```

Here are what each of these properties define:

*   **`$schema`:** Used for defining the supported JSON schema, which will integrate with many code editors to give you on-the-fly hints and error reporting.
*   **`version`:** The `theme.json` schema version you are building for. The latest version is 2 and can always be found in the [`theme.json` Living Reference](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference/theme-json-living/), a document that lists the most up-to-date properties you can set.
*   **`settings`:** Used to define your block controls and color palettes, font sizes, and more.
*   **`styles`:** Used to apply colors, font sizes, custom CSS, and more to the website and blocks.
*   **`customTemplates`:** Metadata for custom templates defined in your theme’s `/templates` folder.
*   **`templateParts`:** Metadata for template parts defined in your theme’s  `/parts` folder.
*   **`patterns`:** An array of pattern slugs to be registered from the [Pattern Directory](https://wordpress.org/patterns/).

You will learn more about these properties and their sub-properties in the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.

## Settings and styles hierarchy

The `theme.json` file in your theme is only one level in a hierarchy of setting and style configurations for a website. This means it can be overridden under certain circumstances.

The order of this hierarchy from lowest to highest is:

*   **WordPress `theme.json`:** WordPress has its own `theme.json` file that defines the default settings and styles.
*   **Theme `theme.json`:** Anything you define in your theme’s `theme.json` file overrides the WordPress defaults.
*   **Child theme `theme.json`:** If active, a child theme’s `theme.json` takes priority over the main or “parent” theme.
*   **User configuration:** Users can further customize how their site works under **Appearance > Editor** in the WordPress admin, and the JSON data is saved in their site’s database. Their choice takes priority over all other levels in the hierarchy.

There are also filter hooks available that let plugin and theme authors override the values dynamically. To learn more about these, check out [How to modify theme.json data using server-side filters](https://developer.wordpress.org/news/2023/07/how-to-modify-theme-json-data-using-server-side-filters/) from the WordPress Developer Blog.

The important thing to remember is that anything configured in your `theme.json` file may not take priority in the hierarchy.