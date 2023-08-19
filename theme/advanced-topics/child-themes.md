# Child Themes

A child theme allows you to change small aspects of your site’s appearance yet still preserve your theme’s look and functionality. To understand how child themes work it is first important to understand the relationship between parent and child themes.

## What is a Parent Theme?

A parent theme is a complete theme which includes all of the [required WordPress template files](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/#required-files) and assets for the theme to work. All themes – excluding child themes – are considered parent themes.

## What is a Child Theme?

As indicated in the overview, a child theme inherits the look and feel of the parent theme and all of its functions, but can be used to make modifications to any part of the theme. In this way, customizations are kept separate from the parent theme’s files. Using a child theme lets you upgrade the parent theme without affecting the customizations you’ve made to your site.

Child themes:

*   make your modifications portable and replicable;

*   keep customization separate from parent theme functions;

*   allow parent themes to be updated without destroying your modifications;

*   allow you to take advantage of the effort and testing put into parent theme;

*   save on development time since you are not recreating the wheel; and

*   are a *great way* to start learning about theme development.

Note: If you are making extensive customizations – beyond styles and a few theme files – creating a parent theme might be a better option than a child theme. Creating a parent theme allows you to avoid issues with deprecated code in the future. This needs to be decided on a case-by-case basis.

## How to Create a Child Theme

### 1\. Create a child theme folder

First, create a new folder in your themes directory, located at `wp-content/themes`.

The directory needs a name. It’s best practice to give a child theme the same name as the parent, but with `-child` appended to the end. For example, if you were making a child theme of `twentyfifteen`, then the directory would be named `twentyfifteen-child`.

### 2\. Create a stylesheet: style.css

Next, you’ll need to create a stylesheet file named `style.css`, which will contain all of the CSS rules and declarations that control the look of your theme. Your stylesheet must contain the below required header comment at the very top of the file. This tells WordPress basic info about the theme, including the fact that it is a child theme with a particular parent.

```css
/*
Theme Name:   Twenty Fifteen Child
Theme URI:    http://example.com/twenty-fifteen-child/
Description:  Twenty Fifteen Child Theme
Author:       John Doe
Author URI:   http://example.com
Template:     twentyfifteen
Version:      1.0.0
License:      GNU General Public License v2 or later
License URI:  http://www.gnu.org/licenses/gpl-2.0.html
Tags:         light, dark, two-columns, right-sidebar, responsive-layout, accessibility-ready
Text Domain:  twentyfifteenchild
*/
```

The following information is required:

*   **Theme Name –** needs to be unique to your theme

*   **Template –** the name of the parent theme directory. The parent theme in our example is the Twenty Fifteen theme, so the Template will be `twentyfifteen`. You may be working with a different theme, so adjust accordingly.

Add remaining information as applicable. The only required child theme file is style.css, but functions.php is necessary to enqueue styles correctly (below).

### 3\. Enqueue stylesheet

The final step is to enqueue the parent and child theme stylesheets, if needed.

Note: In the past, the common method was to import the parent theme stylesheet using `@import` inside `style.css`. This is no longer the recommended practice, as it increases the amount of time it takes style sheets to load. Plus it is possible for the parent stylesheet to get loaded twice.

The ideal way of enqueuing stylesheets is for the parent theme to load both (parent’s and child’s), but not all themes do this. Therefore, you need to examine the code of the parent theme to see what it does and to get the handle name that the parent theme uses. The handle is the first parameter of `[wp_enqueue_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/)`.

There are a few things to keep in mind:

*   the child theme is loaded before the parent theme.

*   everything is hooked to an action with a priority (default is 10) but the ones with the same priority run in the order they were loaded.

*   for each handle, only the first call to `[wp_enqueue_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/)` is relevant (others ignored).

*   the dependency parameter of `[wp_enqueue_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/)` affects the order of loading.

*   without a version number, site visitors will get whatever their browser has cached, instead of the new version.

*   using a function to get the theme’s version will return the active theme’s version (child if there is a child).

*   the functions named `get_stylesheet`\* look for a child theme first and then the parent.

The recommended way of enqueuing the stylesheets is to add a `wp_enqueue_scripts` action and use `[wp_enqueue_style()](https://developer.wordpress.org/reference/functions/wp_enqueue_style/)` in your child theme’s `functions.php`.  
If you do not have one, create a `functions.php` in your child theme’s directory. The first line of your child theme’s `functions.php` will be an opening PHP tag (<?php), after which you can write the PHP code according to what your parent theme does.

If the parent theme loads both stylesheets, the child theme does not need to do anything.

If the parent theme loads its style using a function starting with `get_template`, such as `[get_template_directory()](https://developer.wordpress.org/reference/functions/get_template_directory/)` and `[get_template_directory_uri()](https://developer.wordpress.org/reference/functions/get_template_directory_uri/)`, the child theme needs to load just the child styles, using the parent’s handle in the dependency parameter.

```php
<?php
add_action( 'wp_enqueue_scripts', 'my_theme_enqueue_styles' );
function my_theme_enqueue_styles() {
	wp_enqueue_style( 'child-style',
		get_stylesheet_uri(),
		array( 'parenthandle' ),
		wp_get_theme()->get( 'Version' ) // This only works if you have Version defined in the style header.
	);
}
```

If the parent theme loads its style using a function starting with `get_stylesheet`, such as `[get_stylesheet_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/)` and `[get_stylesheet_directory_uri()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory_uri/)`, the child theme needs to load both parent and child stylesheets. Be sure to use the same handle name as the parent does for the parent styles.

```php
<?php
add_action( 'wp_enqueue_scripts', 'my_theme_enqueue_styles' );
function my_theme_enqueue_styles() {
	$parenthandle = 'parent-style'; // This is 'twentyfifteen-style' for the Twenty Fifteen theme.
	$theme        = wp_get_theme();
	wp_enqueue_style( $parenthandle,
		get_template_directory_uri() . '/style.css',
		array(),  // If the parent theme code has a dependency, copy it to here.
		$theme->parent()->get( 'Version' )
	);
	wp_enqueue_style( 'child-style',
		get_stylesheet_uri(),
		array( $parenthandle ),
		$theme->get( 'Version' ) // This only works if you have Version defined in the style header.
	);
}
```

### 4\. Install child theme

Install the child theme as you install any other theme. You can copy the folder to the site using FTP, or create a zip file of the child theme folder, choosing the option to maintain folder structure, and click on **Appearance > Themes > Add New** to upload the zip file.

### 5\. Activate child theme

Your child theme is now ready for activation. Log in to your site’s Administration Screen, and go to **Administration Screen > Appearance > Themes**. You should see your child theme listed and ready for activation. (If your WordPress installation is multi-site enabled, then you may need to switch to your network Administration Screen to enable the theme (within the Network Admin Themes Screen tab). You can then switch back to your site-specific WordPress Administration Screen to activate your child theme.)

Note: You may need to re-save your menu from **Appearance > Menus** and theme options (including background and header images) after activating the child theme.

## Adding Template Files

Other than the `functions.php` file (as noted above), **any file you add to your child theme will overwrite the same file in the parent theme**.

In most cases, it’s best to create a copy of the template files you want to change from the parent theme, then make your modifications to the copied files, leaving the parent files unchanged. For example, if you wanted to change the code of the parent theme’s `header.php` file, you would copy the file to your child theme folder and customize it there.

Tip: There are several plugins which allow you to detect what specific template is being used on the page at which you are looking.

*   [What The File](https://wordpress.org/plugins/what-the-file/)
*   [What Template File Am I Viewing?](https://wordpress.org/plugins/what-template-file-am-i-viewing/)
*   [Debug Bar](https://wordpress.org/plugins/debug-bar/)

You can also include files in the child theme that are not included in the parent theme. For instance, you might want to create a more specific template than is found in your parent theme, such as a template for a specific page or category archive (e.g. page-3.php would load for a Page with the ID of 3).

See the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Heirarchy Page") page for more information about how WordPress determines which template to use.

## Using functions.php

Unlike `style.css`, the `functions.php` of a child theme does not override its counterpart from the parent. Instead, it is **loaded in addition to the parent’s functions.php**. (Specifically, it is loaded right before the parent’s file.)

In that way, the `functions.php` of a child theme provides a smart, trouble-free method of modifying the functionality of a parent theme. Say that you want to add a PHP function to your theme. The fastest way would be to open its `functions.php` file and put the function there. But that’s not smart: The next time your theme is updated, your function will disappear. But there is an alternative way which is the smart way: you can create a child theme, add a `functions.php` file in it, and add your function to that file. The function will do the exact same job from there too, with the advantage that it will not be affected by future updates of the parent theme. Do not copy the full content of functions.php of the parent theme into functions.php in the child theme.

The structure of `functions.php` is simple: An opening PHP tag at the top, and below it, your bits of PHP. In it you can put as many or as few functions as you wish. The example below shows an elementary `functions.php` file that does one simple thing: Adds a favicon link to the head element of HTML pages.

```php
<?php // Opening PHP tag - nothing should be before this, not even whitespace
// Custom Function to Include
function my_favicon_link() {
	echo '<link rel="shortcut icon" type="image/x-icon" href="/favicon.ico" />' . "\n";
}
add_action( 'wp_head', 'my_favicon_link' );
```

Tip: The fact that a child theme’s functions.php is loaded first means that you can make the user functions of your theme pluggable —that is, replaceable by a child theme— by declaring them conditionally.

if ( ! function\_exists( 'theme\_special\_nav' ) ) {
    function theme\_special\_nav() {
        //  Do something.
    }
}

In that way, a child theme can replace a PHP function of the parent by simply declaring it beforehand.

For more information about what to include in your child theme’s `functions.php` file, read through the [Theme Functions](https://developer.wordpress.org/themes/basics/theme-functions/) page.

## Referencing or Including Other Files

When you need to include files that reside within your child theme’s directory structure, you will need to use [get\_stylesheet\_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/) . Since the `style.css` is in the root of your child theme’s subdirectory, [get\_stylesheet\_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/) points to your child theme’s directory (not the parent theme’s directory). To reference the parent theme directory, you would use [get\_template\_directory()](https://developer.wordpress.org/reference/functions/get_template_directory/) instead.

Below is an example illustrating how to use [get\_stylesheet\_directory()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory/) when referencing a file stored within the child theme directory:

```php
<?php require_once get_stylesheet_directory() . '/my_included_file.php'; ?>
```

Meanwhile, this example uses `[get_stylesheet_directory_uri()](https://developer.wordpress.org/reference/functions/get_stylesheet_directory_uri/)` to display an image that is stored within the `/images` folder in the child theme directory.

```php
<img src="<?php echo get_stylesheet_directory_uri(); ?>/images/my_picture.png" alt="" />
```

Unlike `get_stylesheet_directory()`, which returns a file path, `get_stylesheet_directory_uri()` returns a URL, which is useful for front-end assets.

## Enqueueing Styles and Scripts

Scripts and styles should each be enqueued with their own function, and then those should be wrapped in an action. For more information, read the page on [Including CSS and JavaScript](https://developer.wordpress.org/themes/basics/including-css-javascript/).

WordPress won’t automatically load the stylesheet for your child theme on the front-end. Below is an example of using the `[wp_enqueue_scripts()](https://developer.wordpress.org/reference/functions/wp_enqueue_scripts/)` action hook to call a function that enqueues the child theme’s stylesheet.

```php
<?php
add_action( 'wp_enqueue_scripts', 'my_plugin_add_stylesheet' );
function my_plugin_add_stylesheet() {
	wp_enqueue_style( 'my-style', get_stylesheet_directory_uri() . '/style.css', false, '1.0', 'all' );
}
```

## Special Considerations

### Post Formats

A child theme inherits [post formats](https://developer.wordpress.org/themes/functionality/post-formats/) as defined by the parent theme. But when creating child themes, be aware that using `[add_theme_support('post-formats')](https://developer.wordpress.org/reference/functions/add_theme_support/)` will **override** the formats as defined by the parent theme, not add to it.

### RTL Support

To support RTL languages, add a `rtl.css` file to your child theme, containing:

```css
/*
Theme Name:   Twenty Fifteen Child
Template:     twentyfifteen
*/
```

Even if the parent theme does not have an `rtl.css` file, it’s recommended to add the `rtl.css` file to your child theme. WordPress will auto-load the `rtl.css` file only if `[is_rtl()](https://developer.wordpress.org/reference/functions/is_rtl/)` is true.

### Internationalization

Child themes can be prepared for translation into other languages by using the WordPress [Internationalization API](https://developer.wordpress.org/themes/functionality/internationalization/). There are special considerations regarding internationalization of child themes.

To internationalize a child theme follow these steps:  
1\. Add a languages directory.

*   For example: `twentyfifteen-child/languages/`

2\. Add language files.

*   Your filenames have to be `he_IL.po` & `he_IL.mo` (depending on your language), unlike plugin files which are `domain-he_IL.xx`.

3\. Load a textdomain

*   Use [load\_child\_theme\_textdomain()](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) in `functions.php` during the after\_setup\_theme action.

*   The text domain defined in [load\_child\_theme\_textdomain()](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/) should be used to translate all strings in the child theme.

4\. Use GetText functions to add i18n support for your strings.

#### Example: textdomain

```php
<?php
/**
 * Set up My Child Theme's textdomain.
 *
 * Declare textdomain for this child theme.
 * Translations can be added to the /languages/ directory.
 */
function twentyfifteenchild_theme_setup() {
	load_child_theme_textdomain( 'twentyfifteenchild', get_stylesheet_directory() . '/languages' );
}
add_action( 'after_setup_theme', 'twentyfifteenchild_theme_setup' );
```

At this point, strings in the child theme are ready for translation. To ensure they are properly internationalized for translation, each string needs to have the `twentyfifteenchild` textdomain.

#### Example: gettext functions

Here is an example of echoing the phrase “Code is Poetry”:

```php
<?php esc_html_e( 'Code is Poetry', 'twentyfifteenchild' ); ?>
```

The text domain defined in `[load_child_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_child_theme_textdomain/)` should be used to translate all strings in the child theme. In the event that a template file from the parent them has been included, the textdomain should be changed from the one defined in the parent theme to the one defined by the child theme.