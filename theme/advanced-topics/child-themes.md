# Child Themes

Child themes are extensions of a parent theme. They allow you to modify an existing theme without directly editing that theme’s code. They are often something as simple as a few minor color changes, but they can also be complex and include custom overrides of the parent theme.

In this article, you will learn what parent and child themes are, how to create your own modifications via child themes, and what pieces of a parent theme that can be overridden.

## What are parent and child themes?

### Parent themes

All themes—unless they are specifically a child theme—are technically parent themes. Basically, this means that they are complete themes that can be installed and activated in WordPress. 

Parent themes must have all of the required files, as outlined in the [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/) documentation. Beyond that, you don’t have to do anything special for your theme to *become a parent theme.*

### Child themes

A child theme includes everything from its parent theme by default. This includes the design and any of its functionality. But it can also be used to make customizations to the parent theme without directly modifying the parent theme’s files. This means that you (or your child theme’s users) can still receive updates to the parent theme without losing those modifications.

Child themes:

*   Make your modifications portable and replicable.
*   Keep customizations separate from the parent theme.
*   Allow parent themes to be updated without losing your modifications.
*   Save on development time since you’re only writing the code you need.
*   Are a great way to start your journey toward developing full themes.

It’s worth noting that making extensive customizations from within a child theme can eventually become a management headache. For these more extensive projects, it is often better to fork the original theme and create a full/parent theme of your own. This is something you will need to decide on a case-by-case basis.

### What about grandchild themes?

This is not currently possible. There are only two levels to the standard theme hierarchy: parent and child theme.

However, when building block themes, there are other levels to what is presented on the front end of a site (they are just not a part of the theme layer):

*   WordPress itself (default `theme.json`)
*   Parent theme
*   Child theme
*   User customizations (can override `theme.json`, templates, and patterns)

In a way, the user customization layer works as a “grandchild” theme of sorts. The big difference is that the changes are stored in the database instead of the filesystem.

Outside of that, there is no standard method of creating an installable grandchild theme.

## How to create a child theme

Let’s try creating a child theme of the default [Twenty Twenty-Four](https://wordpress.org/themes/twentytwentyfour/) theme bundled with WordPress. 

### Create a child theme folder

First, your child theme needs a name. This can be whatever you want your theme to be called, but for this guide, let’s name it “Grand Sunrise.”

Now create a new folder in your `wp-content/themes` directory with a kebab-case version of your theme name: `grand-sunrise`.

### Create a style.css

Now you’ll need to create a file named `style.css`. It is the one absolutely necessary file for a child theme to exist. All `style.css` files must contain a File Header and the required header fields, as outlined in the [Main Stylesheet](https://developer.wordpress.org/themes/core-concepts/main-stylesheet/) documentation (please review this doc if you have not already done so).

As noted in the Main Stylesheet documentation, there is an additional field necessary to declare a theme as a child theme. You must add the `Template` header field to the `style.css` File Header:

```css
/**
 * Theme Name: Grand Sunrise
 * Template:   twentytwentyfour
 * ...other header fields
 */
```

There is one caveat to the `Template` field. It must be a 100% match of the folder name of the parent theme, relative to the `wp-content/themes` folder. In this case, we know that the Twenty Twenty-Four theme folder is located at `wp-content/themes/twentytwentyfour`. Therefore, the `Template` value must be `twentytwentyfour`.

### Install and activate child theme

If you are not already working within a development environment with your theme in the `wp-content/themes` folder, you’ll need to move it there now. Depending on your setup, you have several options, but the easiest is to create a ZIP file of your theme and upload it to your test site via **Appearance > Themes > Add New** in your WordPress admin.

For more information on how to add a theme to a WordPress, read [Adding New Themes](https://wordpress.org/documentation/article/work-with-themes/#adding-new-themes) from the WordPress Documentation site.

Once your theme is installed, visit **Appearance > Themes** in your WordPress admin and locate your theme. Click the **Activate** link as shown in this screenshot:

[![WordPress Appearance > Themes screen showing the popup overlay of an empty child theme.](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?resize=2048%2C1055&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/01/child-theme-activate.jpg?ssl=1)

It won’t look any different from your parent theme right now because you haven’t customized it yet. But you have successfully created a child theme.

## Customizing your child theme

When customizing your child theme, all the functionality documented throughout this handbook is fully available to you. But there are a few considerations you should keep in mind, which you’ll learn about in the following sections.

### Loading style.css

This is an optional step and often not needed for block themes because their style handling is generally done via [`theme.json`](https://developer.wordpress.org/themes/global-settings-and-styles/). But it is often necessary if you are building a classic theme. Regardless, you only need to perform this step if you want to ensure that any CSS code in `style.css` is loaded.

Before proceeding with this section, be sure to review the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation, which covers how to load `style.css` in more detail. In that documentation, you will learn how to enqueue stylesheets via the [`wp_enqueue_style()`](https://developer.wordpress.org/reference/functions/wp_enqueue_style/) function on the appropriate hook (note that child themes are loaded before their parent themes).

The ideal method of enqueueing stylesheets is when a parent theme loads both its own `style.css` and the child theme’s `style.css`. But not all themes do this. Therefore, you must examine the code of the parent theme to see which stylesheets it is enqueueing. This is different for every theme, and there are no hard rules.

If the parent theme loads both stylesheets, the child theme does not need to do anything. Its stylesheet will be automatically loaded.

In the case of the Twenty Twenty-Four theme, it doesn’t load a stylesheet at all. So you would have to load your `style.css` via `functions.php` as shown in this code snippet:

```php
add_action( 'wp_enqueue_scripts', 'grand_sunrise_enqueue_styles' );

function grand_sunrise_enqueue_styles() {
	wp_enqueue_style( 
		'grand-sunrise-style', 
		get_stylesheet_uri()
	);
}
```

If the parent theme you are using only loads its own stylesheet, you would also use the above code to load your child theme’s `style.css`.

If the parent theme loads only the active theme’s stylesheet, such as via `get_stylesheet_uri()`, then it will load the child theme’s stylesheet. In this case, you may want to also enqueue the parent theme’s stylesheet via `functions.php`, and your code would look like this:

```php
add_action( 'wp_enqueue_scripts', 'grand_sunrise_enqueue_styles' );

function grand_sunrise_enqueue_styles() {
	wp_enqueue_style( 
		'grand-sunrise-parent-style', 
		get_parent_theme_file_uri( 'style.css' )
	);
}
```

### Templates, parts, and patterns

When building a child theme, you have the option to overwrite any template, part, or pattern that exists in the parent theme by adding a file of the same name in your child theme. *Note: patterns must also have the same registered `Slug` field.*

You can also add brand new templates, parts, and patterns to your child theme, even if they don’t exist in the parent. To learn more about these features, refer to these articles in the handbook:

*   [Templates](https://developer.wordpress.org/themes/templates/)
*   [Patterns](https://developer.wordpress.org/themes/features/block-patterns/)

### Using functions.php

Unlike templates and patterns, the `functions.php` file of a child theme does not override the `functions.php` file in the parent theme. In fact, they are both loaded, with the child being loaded immediately before the parent.

In that way, the `functions.php` of a child theme provides a smart, trouble-free method of modifying the functionality of a parent theme or WordPress. 

Suppose that you wanted to add a PHP function to your theme. The fastest way would be to open its `functions.php` file and put the function there. But that’s not considered a good practice—**the next time your theme is updated, your function will disappear!**

It’s much better to create a child theme and add your custom code to your child theme’s `functions.php` file. The function will do the exact same job from there too, with the advantage that it will not be affected by future updates of the parent theme.

Do not copy code directly from the `functions.php` of a parent theme into your child theme. That will likely lead to fatal errors because of duplicate function names.

To learn more about `functions.php`, check out the [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) documentation.

### Referencing or including other files

Sometimes you need to include or use custom files in your theme. When doing so, you need to make sure that you’re using the function that will give you the correct directory path or URI based on your child theme’s directory.

For example, if you wanted to include another PHP file via your `functions.php`, you would use the [`get_theme_file_path()`](https://developer.wordpress.org/reference/functions/get_theme_file_path/) function. Here is a code snippet that shows including a `functions-helpers.php` file from an `/inc` folder in your child theme:

```php
require_once get_theme_file_path( 'inc/functions-helpers.php' );
```

To learn more about including files, read the [Custom Functionality](https://developer.wordpress.org/themes/core-concepts/custom-functionality/) documentation.

When you need to reference a file by its URL, such as an image or stylesheet, you must use a different function: [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/). Let’s look at an example of using a file named `bunny.jpg` from your theme’s `/assets/images` folder in an `<img>` HTML tag:

```php
<?php $image = get_theme_file_uri( 'assets/images/bunny.jpg' ); ?>

<img src="<?php echo esc_url( $image ); ?>" alt="" />
```

You can find out more about including scripts, styles, images, and other assets from the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation.

### Internationalization

Like parent themes, child themes can also be internationalized and made to work in any language. To learn more, read the [Internationalization](https://developer.wordpress.org/themes/advanced-topics/internationalization/) documentation in the Theme Handbook.

The biggest changes, as noted in the Internationalization documentation, are that you must create a unique text domain and use [`load_child_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) instead of [`load_theme_textdomain()`](https://developer.wordpress.org/reference/functions/load_theme_textdomain/) when manually loading translations.