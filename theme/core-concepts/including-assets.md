# Including Assets

Many block themes do not need to load any assets. For design aspects, specifically, much of this can be handled through the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) system. But there are times when you might need to include a CSS stylesheet, custom JavaScript file, or even other types of media.

If you are familiar with HTML, you might be accustomed to including CSS stylesheets via the `<link rel=”stylesheet”/>` or `<style>` tags. The same might be true for including JavaScript via the `<script>` tag. But you should never manually hard code these HTML elements in your theme. 

WordPress has specific hooks for determining when to load scripts/styles and functions for generating the markup. This ensures that WordPress, any active plugins, and your theme all play nicely together.

In this document, you will learn the necessary functions for generating the proper URL to point to asset files and how to include scripts, styles, and other assets in your theme. 

This documentation is a leap forward in comparison to some of the previous pages in the Core Concepts chapter. You will need some baseline PHP and HTML knowledge to follow along. You must also understand how to use your [theme’s `functions.php` file](https://developer.wordpress.org/themes/core-concepts/custom-functionality/). This is necessary for loading CSS stylesheet and JavaScript files.

## URL and directory path functions

Before including assets, you should become familiar with some of the utility functions that WordPress provides for getting URLs and directory paths within a theme. You should always use these helper functions when including any type of asset to ensure the URL or path is correct.

Three of the primary URL helper functions are:

*   [`get_stylesheet_uri()`](https://developer.wordpress.org/reference/functions/get_stylesheet_uri/): Returns the active theme’s `style.css` file URL.
*   [`get_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/): Returns the active theme’s URL, with an optional `$file` parameter. Falls back to the parent theme if a child theme is active and the file doesn’t exist.
*   [`get_parent_theme_file_uri( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_uri/): Returns the parent theme’s URL, with an optional `$file` path.

For directory paths, which are needed less often for assets, there are two primary functions:

*   [`get_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_theme_file_path/): Returns the active theme’s directory path, with an optional `$file` parameter. Falls back to the parent theme if a child theme is active and the file doesn’t exist.
*   [`get_parent_theme_file_path( $file )`](https://developer.wordpress.org/reference/functions/get_parent_theme_file_path/): Returns the parent theme’s directory path, with an optional `$file` parameter.

## Including CSS

[`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) is the primary function for enqueueing a stylesheet, which tells WordPress that you want to put it in the queue to load. You would use this function within an action hook callback in your `functions.php` file, which you learned about in [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/). You’ll learn which action hooks to use for specific scenarios in the next sections.

Take a look at the function signature:

```php
wp_enqueue_style( 
	string $handle, 
	string $src           = '', 
	string[] $deps        = array(), 
	string|bool|null $ver = false, 
	string $media         = 'all'
);
```

You can use these parameters:

*   **`$handle`** is a unique name/ID for the stylesheet and should be prefixed with your theme slug.
*   **`$src`** is the file URL of your stylesheet. While it is technically an optional parameter, it is required to actually load a specific stylesheet.
*   **`$deps`** is an optional array of other stylesheet handles that your stylesheet is dependent upon.
*   **`$ver`** sets the version number of your stylesheet and is used for cache busting. Defaults to the current WordPress version.
*   **`$media`** is for specifying which type of media to load this stylesheet for, such as `all` (default), `screen`, `print`, or `handheld`.

If you were enqueuing a stylesheet located at `/assets/css/example.css` in your theme, your function call might look like this:

```php
wp_enqueue_style( 
	'theme-slug-example',
	get_parent_theme_file_uri( 'assets/css/example.css' ),
	array(),
	wp_get_theme()->get( 'Version' ),
	'all'
);
```

The above code uses [`wp_get_theme()`](https://developer.wordpress.org/reference/functions/wp_get_theme/) to grab the theme’s version number for cache busting, but you can leave it at the default or use something custom altogether.

### Front-end stylesheets

When loading stylesheets on the front end of a website, you will use the [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) hook for most scenarios.

Let’s assume that you wanted to load your theme’s `style.css` file using the `get_stylesheet_uri()` function. You would do this by adding the following code to your `functions.php` file:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style( 
		'theme-slug-style', 
		get_stylesheet_uri()
	);
}
```

Remember that you can also pass other parameters to the `wp_enqueue_style()` function if needed. The above code is the minimum needed to load the stylesheet.

Let’s further suppose that you wanted to load a second stylesheet located at `/assets/css/primary.css` in your theme. For this, you would use the `get_parent_theme_file_uri()` function to get the correct URL. 

Here is what your code would look like with both stylesheets enqueued:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style(
		'theme-slug-style', 
		get_stylesheet_uri()
	);

	wp_enqueue_style( 
		'theme-slug-primary',
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	);
}
```

### Inline styles

There are times when you might need to add some inline CSS to the `<head>` area on the front end. WordPress has the [`wp_add_inline_style()`](https://developer.wordpress.org/reference/functions/wp_add_inline_style/) function for this specific scenario.

Here is a look at the function signature:

```php
wp_add_inline_style( 
	string $handle, 
	string $data 
);
```

In this case, you must pass in a `$handle` parameter that matches a handle of an existing stylesheet that is enqueued for the page. The `$data` parameter is your custom CSS code.

Let’s extend the code from the previous section by adding a small bit of CSS that sets the body background color to a light gray:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_styles' );

function theme_slug_enqueue_styles() {
	wp_enqueue_style(
		'theme-slug-style', 
		get_stylesheet_uri()
	);

	wp_enqueue_style( 
		'theme-slug-primary',
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	);

	wp_add_inline_style( 
		'theme-slug-primary', 
		'body { background: #eee; }'
	);
}
```

In the `wp_add_inline_style()` function call, the code uses the existing `theme-slug-primary` handle to attach an inline style.

### Editor stylesheets

When creating a theme with custom CSS on the front end, you will almost always want your custom styles to also appear in the editor. This will create a consistent user experience across the site. But WordPress does not automatically load your front-end stylesheets in the editor.

For that, you will need to use the [`add_editor_style()`](https://developer.wordpress.org/reference/functions/add_editor_style/) function:

```php
add_editor_style( array|string $stylesheet = 'editor-style.css' );
```

It accepts a single parameter of `$stylesheet`, which can be a single stylesheet filename or an array of filenames. These can be relative to the theme folder or a full URL.

Note that when using relative URLs, a file in the child theme with the same filename will take priority. That’s why it’s generally best practice to use the full stylesheet URL.

This code snippet shows how to add the active theme’s main `style.css` file as an editor style:

```php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_editor_style( get_stylesheet_uri() );
}
```

If you wanted to add both the `style.css` file and `primary.css` from the earlier examples, you could pass them in as an array:

```php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_editor_style( array(
		get_stylesheet_uri(),
		get_parent_theme_file_uri( 'assets/css/primary.css' )
	) );
}
```

### Block stylesheets

WordPress also includes a [`wp_enqueue_block_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) function for loading per-block stylesheets in the editor and on the front end. This is covered in full detail in the [Block Stylesheets](https://developer.wordpress.org/themes/features/block-stylesheets/) documentation.

For an advanced exploration of block stylesheets, read [Leveraging theme.json and per-block styles for more performant themes](https://developer.wordpress.org/news/2022/12/leveraging-theme-json-and-per-block-styles-for-more-performant-themes/) on the WordPress Developer Blog.

## Including JavaScript

Like stylesheets, WordPress has a primary function for enqueueing JavaScript files: [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/). You would also use this function within an action hook callback in your `functions.php` file, and you’ll learn which hooks to use in the following sections.

Take a look at the function signature:

```php
wp_enqueue_script( 
	string $handle, 
	string $src           = '', 
	string[] $deps        = array(), 
	string|bool|null $ver = false, 
	array|bool $in_footer = false
);
```

You can use these parameters:

*   **`$handle`:** A unique name/ID for the script and should be prefixed with your theme slug.
*   **`$src`:** The file URL of your script. While it is technically an optional parameter, it is required to actually load a specific script
*   **`$deps`:** An optional array of other script handles that your script is dependent upon.
*   **`$ver`:** Sets the version number of your script and is used for cache busting. Defaults to the current WordPress version.
*   **`$in_footer`:** Determines whether to load the script in the header or footer. As of WordPress 6.3, this parameter accepts an array of values:
    *   **`strategy`:** Accepts either `'defer'` (default) or `'async'` to set the script-loading strategy.
    *   **`in_footer`:** A boolean value to determine whether to load the script in the header or footer.

If you were enqueuing a script located at `/assets/js/example.js` in your theme, your function call might look like this:

```php
wp_enqueue_script( 
	'theme-slug-example',
	get_parent_theme_file_uri( 'assets/js/example.js' ),
	array(),
	wp_get_theme()->get( 'Version' ),
	true
);
```

### Front-end JavaScript

When loading stylesheets on the front end of a website, you will use the [`wp_enqueue_scripts`](https://developer.wordpress.org/reference/hooks/wp_enqueue_scripts/) hook for most scenarios.

Suppose you had a custom navigation script located at `assets/js/navigations.js` in your theme. For this, you would use the `get_parent_theme_file_uri()` function to get the correct URL. 

Here is what your function would look like when enqueueing the script:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_scripts' );

function theme_slug_enqueue_scripts() {
	wp_enqueue_script( 
		'theme-slug-navigation',
		get_parent_theme_file_uri( 'assets/js/navigation.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);
}
```

### Inline JavaScript

Sometimes you might want to add some inline JavaScript to the `<head>` area on the front end. WordPress has the [`wp_add_inline_script()`](https://developer.wordpress.org/reference/functions/wp_add_inline_script/) function for this purpose.

Take a look at the function signature:

```php
wp_add_inline_script( 
	string $handle, 
	string $data, 
	string $position = 'after' 
);
```

Like its counterpart for styles, you must attach this to an enqueued script via the `$handle` parameter. The secondary parameter, `$data`, should be the JavaScript code itself. The difference here is the addition of a third parameter, `$position`, which lets you position the inline script before or after the script that it is attached to.

The following code builds on top of the navigation script from the previous section by adding an inline script to it:

```php
add_action( 'wp_enqueue_scripts', 'theme_slug_enqueue_scripts' );

function theme_slug_enqueue_scripts() {
	wp_enqueue_script( 
		'theme-slug-navigation',
		get_parent_theme_file_uri( 'assets/js/navigation.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);

	wp_add_inline_script( 
		'theme-slug-navigation', 
		'console.log( "Testing" );'
	);
}
```

In the `wp_add_inline_script()` function call, the code uses the existing `theme-slug-navigation` handle to attach the inline style.

### Editor JavaScript

When you need to load a JavaScript file for the block editor, you must use the [`enqueue_block_editor_assets`](https://developer.wordpress.org/reference/hooks/enqueue_block_editor_assets/) hook. Note that this is for loading scripts on the admin page itself and not within the content iframe.

Suppose you had an `assets/js/editor.js` file that you needed to load for the editor. Your code should look like this:

```php
add_action( 'enqueue_block_editor_assets', 'theme_slug_enqueue_editor_scripts' );

function theme_slug_enqueue_editor_scripts() {
	wp_enqueue_script( 
		'theme-slug-editor',
		get_parent_theme_file_uri( 'assets/js/editor.js' ),
		array(),
		wp_get_theme()->get( 'Version' ),
		true
	);
}
```

Generally, themes wouldn’t need to load JavaScript for the editor itself. But for advanced use cases, it may be necessary. It is also recommended to integrate with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package for easier management. For more information on how to do this, read [Beyond block styles, part 1: using the WordPress scripts package with themes](https://developer.wordpress.org/news/2023/07/beyond-block-styles-part-1-using-the-wordpress-scripts-package-with-themes/).

### Default WordPress scripts

WordPress bundles many custom and third-party scripts. You should always use these scripts if you need one of them instead of loading a custom version. This ensures that you avoid conflicts with plugins. 

Some of the scripts are referenced in the [`wp_enqueue_script()` documentation](https://developer.wordpress.org/reference/functions/wp_enqueue_script/), but that list may not always be up to date. You can find the full list of included files in [wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php).

## Including images

Block themes will not often need to include images, except in patterns. You will learn more about these in the [Block Patterns](https://developer.wordpress.org/themes/features/block-patterns/) documentation. But for a quick overview, let’s take a look at how to reference an image in your theme.

Assuming you had an image file located at `assets/img/example.webp`, you would use this code to reference the correct URL:

```php
<img src="<?php echo esc_url( get_parent_theme_file_uri( 'assets/img/example.webp' ) ); ?>" alt="" />
```

Note that the above example uses `get_parent_theme_file_uri()`. In most cases, this will be the correct function.

But if you are building a child theme or a theme where you would like to allow other child theme authors to override the image, you can use `get_theme_file_uri()` instead:

```php
<img src="<?php echo esc_url( get_theme_file_uri( 'assets/img/example.webp' ) ); ?>" alt="" />
```

## Including fonts

Typically, you would expect fonts to fall directly under the assets documentation. But WordPress has special methods for loading fonts via the `theme.json` file that integrates with the editor. This documentation is under the [Typography](https://developer.wordpress.org/themes/global-settings-and-styles/settings/typography/) page of the Global Settings and Styles chapter.