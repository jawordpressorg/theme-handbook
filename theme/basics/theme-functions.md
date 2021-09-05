# Theme Functions

The `functions.php` file is where you add unique features to your WordPress theme. It can be used to hook into the core functions of WordPress to make your theme more modular, extensible, and functional.

## What is `functions.php`?

The `functions.php` file behaves like a WordPress plugin, adding features and functionality to a WordPress site. You can use it to call WordPress functions and to define your own functions.

Note: The same result can be produced using either a plugin or `functions.php`. If you are creating new features that should be available no matter what the website looks like, **it is best practice to put them in a plugin**.

There are advantages and tradeoffs to either using a WordPress plugin or using `functions.php`.

A WordPress plugin:

*   requires specific, unique header text;
*   is stored in wp-content/plugins, usually in a subdirectory;
*   only executes on page load when activated;
*   applies to all themes; and
*   should have a single purpose – for example, offer search engine optimization features or help with backups.

Meanwhile, a `functions.php` file:

*   requires no unique header text;
*   is stored in theme’s subdirectory in wp-content/themes;
*   executes only when in the active theme’s directory;
*   applies only to that theme (if the theme is changed, the features can no longer be used); and
*   can have numerous blocks of code used for many different purposes.

Each theme has its own functions file, but only code in the active theme’s `functions.php` is actually run. If your theme already has a functions file, you can add code to it. If not, you can create a plain-text file named `functions.php` to add to your theme’s directory, as explained below.

A [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/) can have its own `functions.php` file. Adding a function to the child functions file is a risk-free way to modify a parent theme. That way, when the parent theme is updated, you don’t have to worry about your newly added function disappearing.

Note: Although the child theme’s `functions.php` is loaded by WordPress right before the parent theme’s `functions.php`, it does not *override* it. The child theme’s `functions.php` can be used to augment or replace the parent theme’s functions. Similarly, `functions.php` is loaded *after any plugin files have loaded*.

With `functions.php` you can:

*   Use WordPress hooks. For example, with the `excerpt_length` filter you can change your post excerpt length (from default of 55 words).
*   Enable WordPress features with `[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)`. For example, turn on post thumbnails, post formats, and navigation menus.
*   Define functions you wish to reuse in multiple theme template files.

Warning: If a WordPress plugin calls the same function, or filter, as you do in your `functions.php`, the results can be unexpected, even causing your site to be disabled.

## Examples

Below are a number of examples that you can use in your functions.php file to support various features. Each of these examples are allowed in your theme if you choose to submit it to the WordPress.org theme directory.

### Theme Setup

A number of theme features should be included within a “setup” function that runs initially when your theme is activated. As shown below, each of these features can be added to your `functions.php` file to activate recommended WordPress features.

Note: It’s important to namespace your functions with your theme name. All examples below use `myfirsttheme_` as their namespace, which should be customized based on your theme name.

To create this initial function, start a new function entitled `myfirsttheme_setup()`, like so:

if ( ! function\_exists( 'myfirsttheme\_setup' ) ) :<br />
/\*\*<br />
\* Sets up theme defaults and registers support for various WordPress features<br />
\*<br />
\*  It is important to set up these functions before the init hook so that none of these<br />
\*  features are lost.<br />
\*<br />
\*  @since MyFirstTheme 1.0<br />
\*/<br />
function myfirsttheme\_setup() {<br />

Note: In the above example, the function myfirsttheme\_setup is started but not closed out. Be sure to close out your functions

#### Automatic Feed Links

Automatic feed links enables post and comment RSS feeds by default. These feeds will be displayed in `<head>` automatically. They can be called using `[add_theme_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)`.

add\_theme\_support( 'automatic-feed-links' );

#### Navigation Menus

Custom [navigation menus](https://developer.wordpress.org/themes/functionality/navigation-menus/ "Navigation Menus") allow users to edit and customize menus in the Menus admin panel, giving users a drag-and-drop interface to edit the various menus in their theme.

You can set up multiple menus in `functions.php`. They can be added using `[register_nav_menus()](https://developer.wordpress.org/reference/functions/register_nav_menus/)` and inserted into a theme using `[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)`, as discussed [later in this handbook](https://developer.wordpress.org/themes/functionality/navigation-menus/). If your theme will allow more than one menu, you should use an array. While some themes will not have custom navigation menus, it is recommended that you allow this feature for easy customization.

<br />
register\_nav\_menus( array(<br />
	'primary'   => \_\_( 'Primary Menu', 'myfirsttheme' ),<br />
	'secondary' => \_\_( 'Secondary Menu', 'myfirsttheme' )<br />
) );<br />

Each of the menus you define can be called later using `[wp_nav_menu()](https://developer.wordpress.org/reference/functions/wp_nav_menu/)` and using the name assigned (i.e. primary) as the `theme_location` parameter.

#### Load Text Domain

Themes can be translated into multiple languages by making the strings in your theme available for translation. To do so, you must use `[load_theme_textdomain()](https://developer.wordpress.org/reference/functions/load_theme_textdomain/)`. For more information on making your theme available for translation, read the [internationalization](https://developer.wordpress.org/themes/functionality/internationalization/ "Internationalization & Text Domains") section.

load\_theme\_textdomain( 'myfirsttheme', get\_template\_directory() . '/languages' );

#### Post Thumbnails

[Post thumbnails and featured images](https://developer.wordpress.org/themes/functionality/featured-images-post-thumbnails/ "Featured Images & Post Thumbnails") allow your users to choose an image to represent their post. Your theme can decide how to display them, depending on its design. For example, you may choose to display a post thumbnail with each post in an archive view. Or, you may want to use a large featured image on your homepage. While not every theme needs featured images, it’s recommended that you support post thumbnails and featured images.

add\_theme\_support( 'post-thumbnails' );

#### Post Formats

[Post formats](https://developer.wordpress.org/themes/functionality/post-formats/ "Post Formats") allow users to format their posts in different ways. This is useful for allowing bloggers to choose different formats and templates based on the content of the post. `add_theme_support()` is also used for Post Formats. This is **recommended**.

add\_theme\_support( 'post-formats',  array ( 'aside', 'gallery', 'quote', 'image', 'video' ) );

[Learn more about post formats.](https://developer.wordpress.org/themes/functionality/post-formats/)

#### Initial Setup Example

Including all of the above features will give you a `functions.php` file like the one below. Code comments have been added for future clarity.

As shown at the bottom of this example, you must add the required `[add_action()](https://developer.wordpress.org/reference/functions/add_action/)` statement to ensure the `myfirsttheme_setup` function is loaded.

<br />
if ( ! function\_exists( 'myfirsttheme\_setup' ) ) :<br />
/\*\*<br />
 \* Sets up theme defaults and registers support for various WordPress features.<br />
 \*<br />
 \* Note that this function is hooked into the after\_setup\_theme hook, which runs<br />
 \* before the init hook. The init hook is too late for some features, such as indicating<br />
 \* support post thumbnails.<br />
 \*/<br />
function myfirsttheme\_setup() {</p>
<p>	/\*\*<br />
	 \* Make theme available for translation.<br />
	 \* Translations can be placed in the /languages/ directory.<br />
	 \*/<br />
	load\_theme\_textdomain( 'myfirsttheme', get\_template\_directory() . '/languages' );</p>
<p>	/\*\*<br />
	 \* Add default posts and comments RSS feed links to &lt;head>.<br />
	 \*/<br />
	add\_theme\_support( 'automatic-feed-links' );</p>
<p>	/\*\*<br />
	 \* Enable support for post thumbnails and featured images.<br />
	 \*/<br />
	add\_theme\_support( 'post-thumbnails' );</p>
<p>	/\*\*<br />
	 \* Add support for two custom navigation menus.<br />
	 \*/<br />
	register\_nav\_menus( array(<br />
		'primary'   => \_\_( 'Primary Menu', 'myfirsttheme' ),<br />
		'secondary' => \_\_('Secondary Menu', 'myfirsttheme' )<br />
	) );</p>
<p>	/\*\*<br />
	 \* Enable support for the following post formats:<br />
	 \* aside, gallery, quote, image, and video<br />
	 \*/<br />
	add\_theme\_support( 'post-formats', array ( 'aside', 'gallery', 'quote', 'image', 'video' ) );<br />
}<br />
endif; // myfirsttheme\_setup<br />
add\_action( 'after\_setup\_theme', 'myfirsttheme\_setup' );<br />

[Expand full source code](#)[Collapse full source code](#)

### Content Width

A content width is added to your `functions.php` file to ensure that no content or assets break the container of the site. The content width sets the maximum allowed width for any content added to your site, including uploaded images. In the example below, the content area has a maximum width of 800 pixels. No content will be larger than that.

<br />
if ( ! isset ( $content\_width) )<br />
    $content\_width = 800;<br />

### Other Features

There are other common features you can include in `functions.php`. Listed below are some of the most common features. Click through and learn more about each of these features.

(Expand this section based on new pages.)

*   [Custom Headers](https://developer.wordpress.org/themes/functionality/custom-headers/)
*   [Sidebars](https://developer.wordpress.org/themes/functionality/sidebars/) (widget areas)
*   Custom Background (needs link)
*   Add Editor Styles (needs link)
*   HTML5 (needs link)
*   Title tag (needs link)

## Your *functions.php* File

If you choose to include all of the functions listed above, this is what your *functions.php* might look like. It has been commented with references to above.

<br />
/\*\*<br />
 \* MyFirstTheme's functions and definitions<br />
 \*<br />
 \* @package MyFirstTheme<br />
 \* @since MyFirstTheme 1.0<br />
 \*/</p>
<p>/\*\*<br />
 \* First, let's set the maximum content width based on the theme's design and stylesheet.<br />
 \* This will limit the width of all uploaded images and embeds.<br />
 \*/<br />
if ( ! isset( $content\_width ) )<br />
	$content\_width = 800; /\* pixels \*/</p>
<p>if ( ! function\_exists( 'myfirsttheme\_setup' ) ) :<br />
/\*\*<br />
 \* Sets up theme defaults and registers support for various WordPress features.<br />
 \*<br />
 \* Note that this function is hooked into the after\_setup\_theme hook, which runs<br />
 \* before the init hook. The init hook is too late for some features, such as indicating<br />
 \* support post thumbnails.<br />
 \*/<br />
function myfirsttheme\_setup() {</p>
<p>	/\*\*<br />
	 \* Make theme available for translation.<br />
	 \* Translations can be placed in the /languages/ directory.<br />
	 \*/<br />
	load\_theme\_textdomain( 'myfirsttheme', get\_template\_directory() . '/languages' );</p>
<p>	/\*\*<br />
	 \* Add default posts and comments RSS feed links to &lt;head>.<br />
	 \*/<br />
	add\_theme\_support( 'automatic-feed-links' );</p>
<p>	/\*\*<br />
	 \* Enable support for post thumbnails and featured images.<br />
	 \*/<br />
	add\_theme\_support( 'post-thumbnails' );</p>
<p>	/\*\*<br />
	 \* Add support for two custom navigation menus.<br />
	 \*/<br />
	register\_nav\_menus( array(<br />
		'primary'   => \_\_( 'Primary Menu', 'myfirsttheme' ),<br />
		'secondary' => \_\_('Secondary Menu', 'myfirsttheme' )<br />
	) );</p>
<p>	/\*\*<br />
	 \* Enable support for the following post formats:<br />
	 \* aside, gallery, quote, image, and video<br />
	 \*/<br />
	add\_theme\_support( 'post-formats', array ( 'aside', 'gallery', 'quote', 'image', 'video' ) );<br />
}<br />
endif; // myfirsttheme\_setup<br />
add\_action( 'after\_setup\_theme', 'myfirsttheme\_setup' );<br />

[Expand full source code](#)[Collapse full source code](#)