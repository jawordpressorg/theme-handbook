# Position

The `settings.position` property in `theme.json` gives you control over the global positioning settings for blocks in WordPress. It’s important to note that this lets you configure the available settings in the user interface, not the position styles.

## Position settings

`position` is an object that’s nested directly within the top-level `settings` property in `theme.json`. Currently, it only lets you set a single property: 

*   **`sticky`:** A boolean value for enabling block support for the **Position: Sticky** option.

Take a look at the `position` property in the context of a `theme.json` file with its default values:

```json
{
	"version": 2,
	"settings": {
		"position": {
			"sticky": false
		}
	}
}
```

### Enabling sticky positioning

Sticky positioning can be particularly useful in theme designs that feature a header that sticks to the top of the screen as the user scrolls down the page. This is one of the primary use cases, but it can also be useful in other scenarios.

Setting a block to the sticky position will stick the block to its most immediate parent when the user scrolls the page. Sticky positioning is only possible if enabled in `theme.json`.

To enable sticky positioning for blocks that support it, set `settings.position.sticky` to `true`:

```json
{
	"version": 2,
	"settings": {
		"position": {
			"sticky": true
		}
	}
}
```

This will enable a new **Position** tab in the block inspector controls (for blocks that support the position feature, such as Group). The control will show a dropdown select with the available position options: **Default** and **Sticky**:

[![WordPress site editor with the Header template part selected. In the right sidebar, the Sticky option is selected for the Position setting.](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/position-sticky-header.jpg?ssl=1)

If you want to create a sticky header, note that you cannot use positioning on the Header template part. You must wrap it with a containing Group block and apply the sticky positioning to the Group.