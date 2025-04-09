# Border

The `settings.border` property in `theme.json` gives you control over the global border settings for blocks in WordPress. It’s important to note that this lets you configure the available settings in the user interface, not the border styles themselves.

Each of the border settings maps to a control at the individual block level and in the **Styles** interface for blocks, letting you curate which controls are available to your theme users:

[![WordPress post editor showing a Post Featured Image block with custom border settings.](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/border-settings.jpg?ssl=1)

## Border settings

WordPress supports four border settings that you can configure via the `settings.border` property in `theme.json`. Each of them allows you to enable or disable a specific border feature and accepts a boolean (`true` or `false`) value:

*   **`color`:** Enables/Disables the border-color picker.
*   **`radius`:** Enables/Disables the border-radius control.
*   **`style`:** Enables/Disables the border-style selector (users have the option of `solid`, `dashed`, or `dotted`).
*   `**width**`: Enables/Disables the border-width input.

By default, all border properties are set to `false`, as shown in this example `theme.json` code:

```json
{
	"version": 2,
	"settings": {
		"border": {
			"color": false,
			"radius": false,
			"style": false,
			"width": false
		}
	}
}
```

As of WordPress 6.3, `color`, `style`, and `width` are intertwined. If any one of them is set to `true`, the others will be available as options within the user interface.

Also, setting the `radius` option to `false` does not work for the Button block. The border-radius control in the editor always appears.