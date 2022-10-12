# Block theme setup

## File structure

Block themes require a `style.css` file and a `templates/index.html` file. A block theme that supports WordPress 5.9 or older also requires an `index.php` file in the root folder.

You need to place all HTML template files inside the `templates` folder. If you place template files in the wrong folder, the theme will not load correctly.  
Template part files are optional. If they are included, they must be placed inside a folder called `parts`.

The theme.json configuration file is optional but strongly recommended. [Learn more about theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/).  
  
In addition to the required files, the theme can include a theme.json, a functions.php file, and any additional PHP files, CSS, images, or JavaScript to enhance the theme.

Example file structure:

patterns (dir)
      - example.php
parts (dir)
      - footer.html
      - header.html
templates(dir)
      - 404.html
      - archive.html
      - index.html (required)
      - singular.html
functions.php
index.php
README.txt
screenshot.png
style.css (required)
theme.json

## Theme setup function

An example setup function inside functions.php in a block theme may include `wp-block-styles` and an editor style:

```
if ( ! function_exists( 'myfirsttheme_setup' ) ) :
/**
 * Sets up theme defaults and registers support for various WordPress features.
 *
 * Note that this function is hooked into the after_setup_theme hook, which runs
 * before the init hook.
 */
function myfirsttheme_setup() {
	// Add support for block styles.
	add_theme_support( 'wp-block-styles' );

	// Enqueue editor styles.
	add_editor_style( 'editor-style.css' );
}
endif; // myfirsttheme_setup
add_action( 'after_setup_theme', 'myfirsttheme_setup' );
```

This is significantly less code than what you may use to [setup a classic theme](https://developer.wordpress.org/themes/basics/theme-functions/#initial-setup-example).

## Theme support

In block themes, the following [theme supports](https://developer.wordpress.org/reference/functions/add_theme_support/) are enabled automatically:

```
add_theme_support( 'post-thumbnails' );
add_theme_support( 'responsive-embeds' );
add_theme_support( 'editor-styles' );
add_theme_support( 'html5', array('style','script', ) );
add_theme_support( 'automatic-feed-links' );
```

Some theme supports are enabled when you include a setting in theme.json. The setting in theme.json takes precedence over `add_theme_support()`.

<table><tbody><tr><td><strong>Theme support</strong></td><td><strong>Theme.json setting</strong></td></tr><tr><td>add_theme_support( ‘editor-font-sizes’, array() );</td><td>settings.typography.fontSizes</td></tr><tr><td>add_theme_support( ‘custom-line-height’ );</td><td>settings.typography.lineHeight</td></tr><tr><td>add_theme_support( ‘align-wide’ );</td><td>settings.layout</td></tr><tr><td>add_theme_support( ‘editor-color-palette’, array() );</td><td>settings.color.palette</td></tr><tr><td>add_theme_support( ‘editor-gradient-presets’, array() );</td><td>settings.color.gradients</td></tr><tr><td>add_theme_support( ‘custom-spacing’ );</td><td>settings.spacing</td></tr><tr><td>add_theme_support( ‘custom-units’, array() );</td><td>settings.spacing.units</td></tr></tbody></table>

## Including CSS for block styles

In addition to [](https://developer.wordpress.org/reference/functions/wp_enqueue_style/)[wp\_enqueue\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) that you can read about in the [theme basics](https://developer.wordpress.org/themes/basics/including-css-javascript/) chapter, you can use [wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) to enqueue styles for blocks. [wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) requires WordPress version 5.9.

A key part of creating block themes is performance. With, `wp_enqueue_block_style()`, the theme only loads the CSS for the selected block when the block is used on the page.  
The additional style is loaded in the editor and the front, after the block style provided by WordPress and the Gutenberg plugin. You can use this method to add block styles that you can not add via theme.json. For example, media queries.

This code example changes the size and text color of the date in the latest comments block. Because this is a `time` HTML element that is nested inside other HTML elements, can not be styled using theme.json.

First, create a new CSS file with the name of the block: `latest-comments.css`.  
Where you place the file depends on how you organize your theme files. In the example, the file is placed inside the folders `assets/CSS/blocks`.

The CSS class for the time element is `wp-block-latest-comments__comment-date`. The prefix and the block name are followed by the partial, separated by two underscores.  
– You can read more about the naming convention for the block editor in the [coding guidelines](https://developer.wordpress.org/block-editor/contributors/code/coding-guidelines/#naming).

The text color and font size are added with CSS custom properties that are generated from theme.json:

```
.wp-block-latest-comments__comment-date {
	color: var(--wp--preset--color--primary);
	font-size: var(--wp--preset--font-size--small);
}
```

Next, enqueue the block style inside the themes setup function.

The block name is placed inside an array to load more than one block style.  
A `foreach` loop walks through each block in the array and creates a handle, src (source), and path argument.  
[wp\_enqueue\_block\_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_block_style/) then enqueues the file using the block name and argument:  
wp\_enqueue\_block\_style( “prefix/blockname”, $args );

In the code example, the prefix is “core” since the style is for a core block. When you style blocks from plugins, you need to adjust the prefix.

```
function myfirsttheme_setup() {
	/*
	 * Load additional block styles.
	 */
	$styled_blocks = ['latest-comments'];
	foreach ( $styled_blocks as $block_name ) {
		$args = array(
			'handle' => "myfirsttheme-$block_name",
			'src'    => get_theme_file_uri( "assets/css/blocks/$block_name.css" ),
			$args['path'] = get_theme_file_path( "assets/css/blocks/$block_name.css" ),
		);
		wp_enqueue_block_style( "core/$block_name", $args );
	}
}
add_action( 'after_setup_theme', 'myfirsttheme_setup' );
```

## Including JavaScript

Please refer to the article [Loading JavaScript](https://developer.wordpress.org/block-editor/how-to-guides/javascript/loading-javascript/) in the block editor handbook.

Changelog:

*   **Created** 2022-01-20