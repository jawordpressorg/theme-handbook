# Converting customizer settings to block patterns

**Prerequisites:** Intermediate knowledge of the Customizer, theme mods, security, and block patterns.

## Example scenario:

*The classic theme has a customizer option for displaying a call to action in the site header.
The call to action is limited to one position, chosen by the theme developer. The user can only turn it on or off, not reposition it or use it more than once.* *The user can only customize a single text input and there are limited color options.*

The original Customizer option has the following settings:

*   Showing or hiding the Call to action (toggle)
*   Call to action text (text input field)
*   Call to action link (url / text input field)
*   Text color picker ( [WP\_Customize\_Color\_Control](https://developer.wordpress.org/reference/classes/wp_customize_color_control/) )
*   Background color picker ( [WP\_Customize\_Color\_Control](https://developer.wordpress.org/reference/classes/wp_customize_color_control/) )

The theme also has to handle sanitizing the Customizer options and adding a Customizer panel or section for the option. Excluding the security measures, the code is approximately 100 lines.

The goal is to convert the Customizer option to a block pattern. By converting the call to action to a block pattern, the user can:

*   Place it anywhere they want, with different content.
*   Change typography, spacing, borders (If these settings are enabled by the theme).
*   Use more color options.
*   Include custom images and other inner blocks.

## Step 1: Recreate the call to action in the block editor

The purpose of recreating the call to action using blocks in the editor, is to get a copy of the HTML, the block markup, that you will use in the pattern. You can use a group, row, or button block depending on your preference.

### Adding existing utility classes

Once you have a copy of the markup, to make the blocks match the existing call to action, re-add any utility CSS classes from the original component.
If your utility class is called “call-to-action\_\_large”, you would add `"className":"call-to-action__large"` to the block comment, and `call-to-action__large` to the `class` attribute of the element.

## Step 2: Register the block pattern

There are two methods for registering or including patterns in your theme. *Both approaches are compatible with classic and block themes*:

*   `patterns/` folder (recommended for block themes, [introduced in WordPress 6.0](https://make.wordpress.org/core/2022/05/02/new-features-for-working-with-patterns-and-themes-in-wordpress-6-0/))
*   PHP registration – uses the [`register_block_pattern()`](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#register_block_pattern)

You can add a new directory named `patterns/` within the root of your block theme and place PHP files within to register patterns. Each individual PHP file will contain a different pattern, e.g. `patterns/my-fun-pattern.php`, `patterns/another-pattern.php`

The following is an example of a simple site footer pattern:

```php
<?php
/**
 * Title: Call to action
 * Slug: theme-slug/call-to-action
 * Categories: featured
 */
?>


<!-- wp:group {"style":{"border":{"width":"4px","style":"solid","radius":"8px"},"color":{"background":"#8550cc"}},"borderColor":"tertiary","layout":{"type":"constrained"},"className":"call-to-action__large"} -->
<div class="wp-block-group call-to-action__large has-border-color has-tertiary-border-color has-background" style="background-color:#8550cc;border-radius:8px;border-style:solid;border-width:4px"><!-- wp:paragraph {"align":"center","style":{"color":{"text":"#fefefe"},"elements":{"link":{"color":{"text":"#fefefe"}}}},"fontSize":"large"} -->
	<p class="has-text-align-center has-text-color has-link-color has-large-font-size" style="color:#fefefe">Call to Action</p>
<!-- /wp:paragraph --></div>
<!-- /wp:group -->
```

## Step 3: Add the customizer option values to the block pattern

First, let’s add the text content and the link. The names of the original customizer options are: `myfirsttheme_action_link` and `myfirsttheme_action_text`.

If the theme already has a function that *returns* the link and the text, the function can be re-used inside the pattern. If not, you need to create a new PHP function that checks if the `theme mod` is used, escapes the content, and returns it:

```php
<?php
function myfirsttheme_action_text() {
	$action_text = '';
	if ( get_theme_mod( 'myfirsttheme_action_link' ) ) {
		$action_text .= '<a href="' . esc_url( get_theme_mod( 'myfirsttheme_action_link' ) ) . '">';
	}
	$action_text .= wp_kses_post( get_theme_mod( 'myfirsttheme_action_text' ) );
	if ( get_theme_mod( 'myfirsttheme_action_link' ) ) {
		$action_text .= '</a>';
	}
	return $action_text;
}
```

Replace the paragraph text *inside the paragraph block* with the function:

```markup
<p class="has-text-align-center has-text-color has-link-color has-large-font-size" style="color:#fefefe">Call to Action</p>
```

Becomes:

```markup
<p class="has-text-align-center has-text-color has-link-color has-large-font-size" style="color:#fefefe">' . myfirsttheme_action_text() . '</p>
```

```javascript
'content' => '
	<!-- wp:group {"style":{"border":{"width":"4px","style":"solid","radius":"8px"},"color":{"background":"#8550cc"}},"borderColor":"tertiary","layout":{"type":"constrained"},"className":"call-to-action__large"} -->
	<div class="wp-block-group call-to-action__large has-border-color has-tertiary-border-color has-background" style="background-color:#8550cc;border-radius:8px;border-style:solid;border-width:4px"><!-- wp:paragraph {"align":"center","style":{"color":{"text":"#fefefe"},"elements":{"link":{"color":{"text":"#fefefe"}}}},"fontSize":"large"} -->
	<p class="has-text-align-center has-text-color has-link-color has-large-font-size" style="color:#fefefe">' . myfirsttheme_action_text() . '</p><!-- /wp:paragraph --></div>
	<!-- /wp:group -->
',
```

Next, you need to get the color codes from the text- and background color options.
The names of the color theme mods are: `myfirsttheme_action_text_color` and `myfirsttheme_action_bgcolor`.

Escape the theme mod with `esc_attr()`, and include the default color of the call to action as your fallback:

```php
esc_attr( get_theme_mod( 'myfirsttheme_action_text_color', '#000' ) );
```

```javascript
"background":"' . esc_attr( get_theme_mod( 'myfirsttheme_action_bgcolor', '#fff' ) ) . '"
```

Remember that each color needs to be replaced both in the block comment and in the `style` attribute of the HTML tag:

```javascript
'content' =>'
	<!-- wp:group {"style":{"border":{"width":"4px","style":"solid","radius":"8px"},"color":{"background":"' . esc_attr( get_theme_mod( 'myfirsttheme_action_bgcolor', '#fff' ) ) . '"}},"borderColor":"tertiary","layout":{"type":"constrained"},"className":"call-to-action__large"} -->
	<div class="wp-block-group call-to-action__large has-border-color has-tertiary-border-color has-background" style="background-color:' . esc_attr( get_theme_mod( 'myfirsttheme_action_bgcolor', '#fff' ) ). ';border-radius:8px;border-style:solid;border-width:4px"><!-- wp:paragraph {"align":"center","style":{"color":{"text":"' . esc_attr( get_theme_mod( 'myfirsttheme_action_text_color', '#000' ) ) . '"},"elements":{"link":{"color":{"text":"' . esc_attr( get_theme_mod( 'myfirsttheme_action_text_color', '#000' ) ). '"}}}},"fontSize":"large"} -->
	<p class="has-text-align-center has-text-color has-link-color has-large-font-size" style="color:' . esc_attr( get_theme_mod( 'myfirsttheme_action_text_color', '#000' ) ). '">' . myfirsttheme_action_text() . '</p><!-- /wp:paragraph -->
	</div>
	<!-- /wp:group -->
',
```

## Step 4: Display the block pattern

If you are converting the themes header area to an editable template part, you can include the pattern in the template part with the pattern block:

```markup
<!-- wp:pattern {"slug":"myfirsttheme/call-to-action"} /-->
```

If you are keeping the PHP header template, you can, if you like, render the block pattern with [d`o_blocks()`](https://developer.wordpress.org/reference/functions/do_blocks/):

```php
echo do_blocks( '<!-- wp:pattern {"slug":"myfirsttheme/call-to-action"} /-->' );
```

After this, you can remove the Customizer options from your theme: The user’s original values are still stored in the database. The user can customize the block in the editor instead of the Customizer.

Changelog:

*   **Updated** 2023-03-08 Updated code examples to reflect WordPress 6.1 block markup.
