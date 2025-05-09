# Build Process

A build process is a method of converting source code files into a final build/production version that can be read by the computer. In particular, themes will most often be minifying or converting source code into CSS or JavaScript so that they can be read by the browser.

When creating a WordPress theme, you may find yourself in need of a build process to handle more complex projects. There are many systems to choose from, and you can use whatever you prefer. But WordPress also offers a standard package that you can be assured is continually updated and should cover most of your needs.

In this article, you will learn how to integrate with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package to handle your theme’s build process.

## Prerequisites

Most of WordPress theme development is pretty much plug and play. You just need a code editor and an install of WordPress in some type of development environment as outlined in [Tools and Setup](https://developer.wordpress.org/themes/getting-started/tools-and-setup/). But to work with a build process, there are some other requirements:

*   You need to have [Node.js and npm installed](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) on your local machine.
*   A basic [understanding of webpack](https://webpack.js.org/concepts/) is also highly recommended.
*   Some familiarity with the [`@wordpress/scripts`](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/) package (read [Getting started with wp-scripts](https://developer.wordpress.org/block-editor/getting-started/devenv/get-started-with-wp-scripts/) in the Block Editor Handbook).

These are more advanced tools than what is normally required to build themes, but they are necessary if you want to work with the standard WordPress build process.

## Setting up your files and folders

The `@wordpress/scripts` package was originally created for block development, but it evolved to also work with themes over time. By default, it expects that development files live in the `/src` folder and will output build files in the `/build` folder. Because most theme authors utilize a custom system for working with assets, this guide will show you how to do that.

For the examples that follow, you will use this structure within your theme folder:

*   `public/`
*   `resources/`
    *   `js/`
        *   `editor.js`
    *   `scss/`
        *   `editor.scss`
        *   `screen.scss`
*   `package.json`
*   `webpack.config.js`

## Installing the WordPress scripts package

Once you have your files and folders set up, you need to install the correct packages on your local machine.

First, open your theme’s `package.json` file and add the following code:

```json
{
	"name": "your-project-name",
	"scripts": {
		"start": "wp-scripts start --webpack-src-dir=resources --output-path=public",
		"build": "wp-scripts build --webpack-src-dir=resources --output-path=public"
	}
}
```

The `@wordpress/scripts` package has several other [available scripts](https://developer.wordpress.org/block-editor/reference-guides/packages/packages-scripts/#available-scripts) that you can add, but you will definitely need `start` and `build`.

Now open your command line tool on your computer, navigate to your theme folder, and input the following command:

```bash
npm install @wordpress/scripts path webpack-remove-empty-scripts --save-dev
```

That command installs three packages:

*   `@wordpress/scripts`
*   `path`
*   `webpack-remove-empty-scripts`

The latter two are third-party packages, but they are useful for integrating with webpack in the next step.

## Configuring webpack

The `@wordpress/scripts` package is built on top of webpack. If you were building a block, everything would already be in place for you. However, because you are building a theme, you need to overwrite some of the default configuration of the `@wordpress/scripts` package with your own.

That’s where your theme’s custom `webpack.config.js` file comes in. There two primary things you need to configure:

*   The entry points for your custom CSS and JavaScript files (those in the code below correspond to the file structure in this article).
*   The `webpack-remove-empty-scripts` plugin so that there are no leftover `.js` files mapped to your CSS.

Add the following code to your `webpack.config.js` file:

```javascript
// WordPress webpack config.
const defaultConfig = require( '@wordpress/scripts/config/webpack.config' );

// Plugins.
const RemoveEmptyScriptsPlugin = require( 'webpack-remove-empty-scripts' );

// Utilities.
const path = require( 'path' );

// Add any new entry points by extending the webpack config.
module.exports = {
	...defaultConfig,
	...{
		entry: {
			'js/editor':  path.resolve( process.cwd(), 'resources/js',   'editor.js'   ),
			'css/screen': path.resolve( process.cwd(), 'resources/scss', 'screen.scss' ),
			'css/editor': path.resolve( process.cwd(), 'resources/scss', 'editor.scss' ),
		},
		plugins: [
			// Include WP's plugin config.
			...defaultConfig.plugins,

			// Removes the empty `.js` files generated by webpack but
			// sets it after WP has generated its `*.asset.php` file.
			new RemoveEmptyScriptsPlugin( {
				stage: RemoveEmptyScriptsPlugin.STAGE_AFTER_PROCESS_PLUGINS
			} )
		]
	}
};
```

## Using the WordPress scripts package

To use the WordPress scripts package to process your assets, you can run one of two commands in your command line tool:

*   `start`: Builds the development version of your files and activates “watch” mode, which will process any code changes while enabled.
*   `build`: Builds the production version of your files.

Now open your command line tool and run the `start` command:

```bash
npm run start
```

It should automatically process your files from the `/resources` folder and place them in the `/public` folder with this structure:

*   `public/`
    *   `js/`
        *   `editor.js`
        *   `editor.asset.php`
    *   `scss/`
        *   `editor.scss`
        *   `editor.asset.php`
        *   `screen.scss`
        *   `screen.asset.php`

You’ll now see new `*.asset.php` files generated for each of your CSS and JavaScript files. These will contain metadata about each asset file that you can use when loading your files. This is covered in the “Loading scripts and styles” section below.

To disable the `start` command, type `Ctrl + C` (on either Windows or Mac) of your command line tool.

Once you’re ready to do a final production build of your files, run this command in your command line tool:

```bash
npm run build
```

## Loading scripts and styles

The methods for loading scripts and styles are already covered in depth in the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation in this handbook. You should already be familiar with how to do this before proceeding with the next steps.

The documentation below is primarily geared towards teaching you how the `*.asset.php` file is generated for each asset. In each file, you will see an array that looks similar to the following snippet:

```php
<?php return array('dependencies' => array('wp-block-editor'), 'version' => '2eae4c519afeff2a8c77');
```

In particular, the array will have two pieces of metadata that you can use in any `wp_enqueue_*()` functions:

*   **`dependencies`:** An array of dependencies that your script/style rely on.
*   **`version`:** A version number that you can use for cache busting.

Because the file returns the array, you can use PHP’s `include` to assign the array to a variable in your code. The following example shows getting the array for the `screen.asset.php` file:

```php
$asset = include get_theme_file_path( 'public/css/screen.asset.php' );
// Returns: array( 'dependencies' => array(), 'version' => '0000' );
```

When loading a script or style using either [`wp_enqueue_script()`](https://developer.wordpress.org/reference/functions/wp_enqueue_script/) or [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/), you can pass `$asset['dependencies']` and `$asset['version']` to the corresponding parameters in the functions.

Try adding the following code to your theme’s `functions.php` file to load the assets that you’ve previously defined:

```php
// Load front-end assets.
add_action( 'wp_enqueue_scripts', 'themeslug_assets' );

function themeslug_assets() {
	$asset = include get_theme_file_path( 'public/css/screen.asset.php' );

	wp_enqueue_style(
		'themeslug-style',
		get_theme_file_uri( 'public/css/screen.css' ),
		$asset['dependencies'],
		$asset['version']
	);
}

// Load editor stylesheets.
add_action( 'after_setup_theme', 'themeslug_editor_styles' );

function themeslug_editor_styles() {
	add_editor_style( [
		get_theme_file_uri( 'public/css/screen.css' )
	] );
}

// Load editor scripts.
add_action( 'enqueue_block_editor_assets', 'themeslug_editor_assets' );

function themeslug_editor_assets() {
	$script_asset = include get_theme_file_path( 'public/js/editor.asset.php'  );
	$style_asset  = include get_theme_file_path( 'public/css/editor.asset.php' );

	wp_enqueue_script(
		'themeslug-editor',
		get_theme_file_uri( 'public/js/editor.js' ),
		$script_asset['dependencies'],
		$script_asset['version'],
		true
	);

	wp_enqueue_style(
		'themeslug-editor',
		get_theme_file_uri( 'public/css/editor.css' ),
		$style_asset['dependencies'],
		$style_asset['version']
	);
}
```