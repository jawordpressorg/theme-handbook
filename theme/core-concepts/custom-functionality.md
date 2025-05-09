# Custom Functionality (functions.php)

This document will introduce you to the `functions.php` file. It is one of the optional standard files you first learned about in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/). Both block and classic themes can utilize it.

The following will introduce you to the core concepts around using PHP within `functions.php`, but it will not teach you the PHP programming language itself. You can visit the official [PHP documentation](https://www.php.net/) for more information on how to write your own PHP code.

Throughout the handbook, you will encounter more examples where you will add custom functionality, so getting the basics down is important. You can jump into more advanced PHP examples in the [Features](https://developer.wordpress.org/themes/features/), [Advanced Topics](https://developer.wordpress.org/themes/advanced-topics/), and [Classic Themes](https://developer.wordpress.org/themes/classic-themes/) chapters.

## What is functions.php?

The `functions.php` essentially acts like a WordPress plugin, letting you add custom PHP functions, classes, interfaces, and more. It opens up the entirety of the PHP programming language to your theme.

WordPress automatically loads the `functions.php` file (if it exists) as soon as it loads the theme on all page views on both the admin and front-end of the website. So it provides you with a lot of power to build unique features around WordPress.

Just because you *can* build plugin-like features in a theme doesn’t mean you always should, particularly if you are distributing your theme to others to use. If you are creating features that should be available regardless of the site’s design, **it is best practice to put the code in a plugin**. The rule of thumb is that themes should only deal with the site’s design.

While all themes can have a custom `functions.php` file, WordPress will only load the currently active theme’s.

The only caveat to that rule is when a child theme is active. In that case, WordPress loads the child theme’s `functions.php` just before loading the parent theme’s `functions.php`. You can learn more about [child themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) in the Advanced Topics chapter.

## Common uses for functions.php

Because the `functions.php` file lets you write any PHP, you will often see themes with wildly different code, organizational systems, naming conventions, and more. The deeper your understanding of PHP, the easier it will be to follow the code from other themes.

The following are some uses you will often find in a theme’s `functions.php` file. 

### Adding actions or filters to hooks

Hooks are the entry point to extending WordPress’ functionality, providing you with a way to inject custom code or filter data. Think of them as a way for themes (and plugins) to communicate directly with WordPress.

WordPress’ hooks system offers two different methods for executing your code during the page loading process:

*   [**Action hooks**](https://developer.wordpress.org/plugins/hooks/actions/) allow you to run a custom action callback and “act on” the information that it receives.
*   [**Filter hooks**](https://developer.wordpress.org/plugins/hooks/filters/) let you filter data via a custom filter callback and manipulate it.

Technically, hooks are a part of the Plugin API, and you can [read the documentation](https://developer.wordpress.org/plugins/hooks/) on them in the Plugin Handbook.

Despite being in the Plugin API, hooks are also extremely useful in the context of themes. Like plugins, you should always run your code on a hook so that it performs its functionality at the appropriate point in the load process.

Throughout this handbook, you will see examples of adding features or functionality from `functions.php`, and these examples will always use a hook. Familiarizing yourself with their documentation will make it easier to understand PHP code in the handbook.

### Theme setup function

One common use case for many themes is adding a setup function, which is generally used to register theme-supported features with WordPress. This is almost always executed on the `after_setup_theme` action hook, which is the first hook available after a theme’s `functions.php` file has been loaded.

To test this, open your theme’s `functions.php` file (create one if it doesn’t exist), and add the following PHP code:

```php
<?php
add_action( 'after_setup_theme', 'theme_slug_setup' );

function theme_slug_setup() {
	add_theme_support( 'wp-block-styles' );
}
```

This code adds support for WordPress’ more-opinionated block styles to your theme. You do not have to use this; it is merely serving as an example of what a setup function might look like.

Setup functions are more common in classic themes. When using a block theme, the theme is often automatically opted into the features needed. You can find a list of theme-supported features here:

*   [Function Reference: `add_theme_support()`](https://developer.wordpress.org/reference/functions/add_theme_support/)
*   [Block Editor Handbook: Theme Support](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-support/)

### Loading scripts and styles

If you are familiar with HTML, you will likely have come across adding JavaScript via the `<script>` tag or stylesheets via the `<link rel=”stylesheet”/>` or `<style>`  tags.

WordPress provides helper functions and specific action hooks for loading scripts and styles. This ensures that they are injected at the appropriate place in the document output. WordPress creates the appropriate HTML markup for you.

You can learn more about loading scripts and styles in the [Including Assets](https://developer.wordpress.org/themes/core-conepts/including-assets/) documentation.

It is not uncommon when building block themes to have no need of including additional scripts/styles. Some themes rely entirely on [Global Settings and Styles](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) for the front-end design.

## Including other PHP files

WordPress will automatically load your theme’s `functions.php` for you, but you are not limited to only adding custom PHP code in that file. You can load other files with PHP interfaces, classes, traits, and functions from elsewhere in your theme.

As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), some themes include a custom folder named `/inc` (or any custom folder) to store custom PHP files. Let’s assume you had an `/inc/helpers.php` file for custom helper functions, you could load it via `functions.php` using the `get_parent_theme_file_path()` function:

```php
include get_parent_theme_file_path( 'inc/helpers.php' );
```

Generally speaking, you should use this function to get the correct directory path to any PHP file you need to load.

Alternatively, if you wanted to allow a child theme to override the file with a fallback to the parent theme, you could use `get_theme_file_path()` instead:

```php
include get_theme_file_path( 'inc/helpers.php' );
```

It’s not standard practice to let child theme’s override files with PHP functions or classes, but there are use cases where it’s needed.

## Avoid closing ?> tags at the end of files

This section could otherwise be titled “How to avoid the dreaded WordPress *white screen of death*.”

There are various reasons that you might see a broken site with nothing but a white screen. One of those reasons is when the `functions.php` file (or any PHP file) has whitespace following its closing `?>` tag like this:

```php
<?php
// some code...
?>
 
```

Many editor configurations will automatically add an extra line at the end of files (a common development practice). When you add a closing `?>` tag at the end of the file, it can be easy to miss this extra whitespace, which may cause the “white screen of death” in some environments.

The easiest way to avoid this issue is to leave the closing `?>` tag out altogether, which is perfectly valid PHP and standard practice. The above code should be written as:

```php
<?php
// some code...
 
```