# Custom block styles

A custom block style is an optional style for a block that you can preview and select from the block settings sidebar in the editor. An example of a block style is the image block with rounded corners.

For a style to be available you must first register it using a unique `name`, a `label`, and CSS.  
WordPress uses the registered `name` parameter to generate a CSS class that is added to the block.  
If the name of your block style is `rounded-corners`, the CSS class will be `is-style-rounded-corners`.

You can register the custom block style using JavaScript or PHP.

## Register custom block styles with PHP

The PHP function used to register custom block styles is called [register\_block\_style](https://developer.wordpress.org/reference/functions/register_block_style/). This function is available from WordPress 5.3.0.

When you register the block style with PHP you can choose between adding CSS inline during registration, or place your CSS in a stylesheet that you [enqueue](https://developer.wordpress.org/themes/basics/including-css-javascript/).

The arguments for the function are:

*   **block\_name**: A string with the prefix and slug of the block. For example `core/post-featured-image`.
*   **style\_properties**: An array with the following parameters:
    *   **name** (required)
    *   **label** (required). The visible name in the editor. This text needs to be wrapped inside a translation function.
    *   **is\_default** (optional). Boolean, set the value to `true` to make the style the default.
    *   **inline\_style** (optional). A string containing the CSS you want to apply.
    *   **style\_handle** (optional). A string with the handle of a CSS file that you are enqueuing.
    

**Step 1:** Create a callback function and initialize it with the `init` action hook:

```php
add_action( 'init', 'themeslug_register_block_styles' );

function themeslug_register_block_styles() {

}
```

**Step 2:** Inside the function, add the prefix and the block name to register\_block\_style:

```php
 register_block_style(
        'core/quote',
);
```

**Step 3**: Include the required parameters `name` and `label` inside an array:

```php
 register_block_style(
        'core/quote',
        array(
            'name' => 'blue-quote',
            'label' => __( 'Blue Quote', 'textdomain' ),
        )
    );
```

**Step 4:** Include optional parameters. The example below uses inline CSS.

```php
register_block_style(
	'core/quote',
	array(
		'name'         => 'blue-quote',
		'label'        => __( 'Blue Quote', 'textdomain' ),
		'is_default'   => true,
		'inline_style' => '.wp-block-quote.is-style-blue-quote { color: blue; }',
	)
);
```

Complete example:

```php
add_action( 'init', 'themeslug_register_block_styles' );

function themeslug_register_block_styles() {
    register_block_style(
        'core/quote',
        array(
            'name'         => 'blue-quote',
            'label'        => __( 'Blue Quote', 'textdomain' ),
            'is_default'   => true,
            'inline_style' => '.wp-block-quote.is-style-blue-quote { color: blue; }',
        )
    );
}
```

## Register custom block styles with JavaScript

You register block styles with JavaScript using `registerBlockStyle` which is part of the wp.blocks package. `[wp.blocks](https://github.com/WordPress/gutenberg/blob/trunk/packages/blocks/README.md)` is an official WordPress JavaScript package that is used in the block editor.

The block editor packages can be used in several different ways, including as separate `npm` packages.  
In these examples you will use wp.blocks as dependency for your JavaScript file. – You will not need to install any additional tools, and you will not need a build process for your JavaScript.

The parameters of `registerBlockStyle` are the block name (prefix and slug), the style variation name, and the label.

**Step 1:** Create a new JavaScript file for your block style. In the example, the file name is `block-style.j`s.  
First add `registerBlockStyle` and the block name (prefix and slug):

```javascript
wp.blocks.registerBlockStyle('core/quote');
```

**Step 2:** Include the required `name parameter:`

```javascript
wp.blocks.registerBlockStyle('core/quote', {
	name: 'blue-quote',
});
```

**Step 3:** Add the text for the visible label. To make the label translation ready you need to use a second JavaScript package called  wp.i18n, and wrap the text inside `__()`:

```javascript
wp.blocks.registerBlockStyle('core/quote', {
	name: 'blue-quote',
	label: wp.i18n.__('Blue', 'textdomain')
});
```

That is all the code you need in the JavaScript file.

**Step 4:** Next, enqueue your JavaScript file for the editor using the [enqueue\_block\_editor\_assets](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) hook and [](https://developer.wordpress.org/reference/functions/wp_enqueue_script/)[wp\_enqueue\_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) . Add the two packages `wp-blocks` and `wp-i18n` as dependencies:

```php
function themeslug_editor_assets() {
	wp_enqueue_script(
		'themeslug-block-styles-script',
		get_theme_file_uri( '/block-style.js' ),
		array( 'wp-blocks', 'wp-i18n' )
	);
}
add_action( 'enqueue_block_editor_assets', 'themeslug_editor_assets' );
```

**Step 5:** One more step is needed to make the label translation ready. Below `wp_enqueue_script`, add [](https://developer.wordpress.org/reference/functions/wp_set_script_translations/)[wp\_set\_script\_translations()](https://developer.wordpress.org/reference/functions/wp_set_script_translations/) . The first paramater is the handle, the slug for your script, the second is the theme text domain:

```php
function themeslug_editor_assets() {
	wp_enqueue_script(
		'themeslug-block-styles-script',
		get_theme_file_uri( '/block-style.js' ),
		array( 'wp-blocks', 'wp-i18n' )
	);
	wp_set_script_translations( 'themeslug-block-styles-script', 'textdomain' );
}
add_action( 'enqueue_block_editor_assets', 'themeslug_editor_assets' );
```

**Step 6:** Add your CSS to the editor and the front of the website.  
You can use the selector (`.is-style-blue-quote`) and add your CSS to a file that you are already enqueuing, for example style.css file and the editor stylesheet.  
  
In this example, the CSS is in a separate file that is enqueued with the [enqueue\_block\_assets](https://developer.wordpress.org/reference/hooks/enqueue_block_assets/) hook. Enqueue\_block\_assets() loads the styles in both the editor and the front.

```php
function themeslug_block_styles() {
	wp_enqueue_style(
		'themeslug-block-styles',
		get_theme_file_uri( '/custom-block-styles.css' ),
		false
	);
}
add_action( 'enqueue_block_assets', 'themeslug_block_styles' );
```

##   
Deregistering custom block styles

Custom block styles can also be deregistered. The three most important things to remember when deregistering custom block styles are:

*   Styles registered with PHP can only be deregistered with PHP.
*   Styles registered with JavaScript can only be deregistered with JavaScript, and needs to be deregistered at the correct time.

### Deregistering custom block styles using PHP

The PHP function [](https://developer.wordpress.org/reference/functions/unregister_block_style/)[unregister\_block\_style()](https://developer.wordpress.org/reference/functions/unregister_block_style/) requires the block name (prefix and slug) followed by the name of the block style:

```php
unregister_block_style( 'core/quote', 'blue-quote' );
```

### Deregistering custom block styles using JavaScript

**Step 1:** Create a new JavaScript file which uses `unregisterBlockStyle` from the `wp.blocks` package.  
Add the block name (prefix and slug) followed by the name of the block style.

```javascript
wp.blocks.unregisterBlockStyle( 'core/quote', 'blue-quote' );
```

**Step 2:** Make sure that the code runs at the correct time by wrapping it inside `wp.domReady()`.  
*You can learn more about why this is needed in the Styles chapter in [the block editor handbook](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-styles/).*

```javascript
wp.domReady( function () {
    wp.blocks.unregisterBlockStyle( 'core/quote', 'blue-quote' );
} );
```

**Step 3:** Enqueue the JavaScript file with [wp\_enqueue\_script](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) on the [enqueue\_block\_editor\_assets](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) hook and the following packages as dependencies: `wp-block`s, `wp-dom-ready`, and `wp-edit-post`:

```php
function themeslug_unregister_block_style() {
	wp_enqueue_script(
		'themeslug-unregister',
		get_stylesheet_directory_uri() . '/unregister.js',
		array( 'wp-blocks', 'wp-dom-ready', 'wp-edit-post' )

	);
}
add_action( 'enqueue_block_editor_assets', 'themeslug_unregister_block_style' );
```

## Resource links

*   [Creating custom block styles in WordPress themes, from the Developer Blog](https://developer.wordpress.org/news/2023/02/creating-custom-block-styles-in-wordpress-themes/)
*   [Styles chapter in the block editor handbook](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-styles/)

Changelog:

*   **Created** 2023-02-03