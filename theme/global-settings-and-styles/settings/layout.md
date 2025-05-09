# Layout

The `settings.layout` property in `theme.json` is an object that stores layout-related settings that you can configure. At the moment, it is used for setting “content” and “wide” widths, but it could also be used for other settings in the future.

In this document, you will learn what the `layout` property is used for and how you can use it in your theme.

## Layout settings

`layout` is an object that’s nested directly within the top-level `settings` property in `theme.json`. Within that object, you can define two settings:

*   `**contentSize**`: A valid CSS length value for defining the default width for content. It is typically used for controlling the width of the post content and related areas on the page.
*   **`wideSize`:** A valid CSS length value for defining the default wide alignment width, which is generally between the content size and full viewport width.

Take a look at the `layout` property in the context of a `theme.json` file with its default values:

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "",
			"wideSize": ""
		}
	}
}
```

### Content size

The `settings.layout.contentSize` property is primarily useful for defining the width of a site’s content area. Think of this as the default width of your site. You can break outside of this by applying the “wide” (below) or “full” width to a block. The content width is merely the foundation.

In almost any design, you will want to limit this width to something that is comfortable to read, especially if the content is going to include text. This is a value that you will need to determine for yourself, but a good rule of thumb is that you should have 45-75 characters of text per line (though some guidelines differ slightly on the number range). Of course, your default font-family and font-size are crucial pieces to figuring this out.

Try configuring a content size in your `theme.json` file:

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "40rem"
		}
	}
}
```

If you open a template in the **Site Editor**, you can use it to define the layout for various blocks. In the screenshot below, you can see that the Post Content block has the **Inner blocks use content width** option selected under the **Layout** tab:

[![WordPress post editor with a Post Content block selected, showing its inner content limited to the content width.](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/content-size.jpg?ssl=1)

What this setting does is tell WordPress that any nested blocks within the Post Content block should be set to the `40rem` value defined for `settings.layout.contentSize` in `theme.json`.

### Wide Size

The `settings.layout.wideSize` property defines a width for “wide” blocks. To be useful, wide blocks must be nested within a block that is telling WordPress that its inner blocks should be limited to the “content” size. Wide-aligned blocks are meant to “break outside” of their parent block.

Not every theme will benefit by having a wide size. Depending on the design, a theme’s layout may simply not have additional room for blocks to break out of their container. In those cases, you do not need to set this value.

For theme designs that can accommodate wide blocks (typical of sidebar-less designs), you will want to set this to a value that is greater than `settings.layout.contentWidth`. But it shouldn’t stretch to the width of the full screen (e.g., `100vw`). WordPress has a separate full-width setting that you can use for that.

Try adding a custom `settings.layout.wideSize` to your `theme.json` file (remember, you need a set content size for this to be useful):

```json
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "40rem",
			"wideSize": "64rem"
		}
	}
}
```

Now open your **Site Editor** in the WordPress admin and edit a template. First, add a **Group** block with the **Inner blocks use content width** option enabled. Then, stick another block within it and select the **Wide width** option.

In the screenshot below, you can see the Post Featured Image block nested within a Group block. It breaks out of its parent container but the other post-related blocks are limited to the content width:

[![WordPress site editor with the Post Featured Image block selected and set to "wide width".](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/wide-size.jpg?ssl=1)