# Custom Logo

## What is a Custom Logo?

Using a custom logo allows site owners to upload an image for their website, which can be placed at the top of their website. It can be uploaded from **Appearance > Header**, in your admin panel. The custom logo support should be added first to your theme using `add_theme_support()`, and then be called in your theme using `the_custom_logo()`. A custom logo is **optional**, but theme authors should use this function if they include a logo to their theme.

### Adding Custom Logo support to your Theme

To enable the use of a custom logo in your theme, add the following to your `functions.php` file:

```php
add_theme_support( 'custom-logo' );
```

When enabling custom logo support, you can configure five parameters by passing along arguments to the `add_theme_support()` function using an array:

```php
function themename_custom_logo_setup() {
	$defaults = array(
		'height'               => 100,
		'width'                => 400,
		'flex-height'          => true,
		'flex-width'           => true,
		'header-text'          => array( 'site-title', 'site-description' ),
		'unlink-homepage-logo' => true, 
	);
	add_theme_support( 'custom-logo', $defaults );
}
add_action( 'after_setup_theme', 'themename_custom_logo_setup' );
```

The [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that the custom logo support is registered after the theme has loaded.

*   `height`  
    Expected logo height in pixels. A custom logo can also use built-in image sizes, such as `thumbnail`, or register a custom size using [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/).
*   `width   `Expected logo width in pixels. A custom logo can also use built-in image sizes, such as `thumbnail`, or register a custom size using [`add_image_size()`](https://developer.wordpress.org/reference/functions/add_image_size/).
*   `flex-height`  
    Whether to allow for a flexible height.
*   `flex-width   `Whether to allow for a flexible width.
*   `header-text   `Classes(s) of elements to hide. It can pass an array of class names here for all elements constituting header text that could be replaced by a logo.
*   `unlink-homepage-logo`  
    *If the `[unlink-homepage-logo](https://make.wordpress.org/core/2020/07/28/themes-changes-related-to-get_custom_logo-in-wordpress-5-5/)` parameter is set to true,* logo images inserted using `get_custom_logo()` or `the_custom_logo()` will no longer link to the homepage when visitors are on that page. In an effort to maintain the styling given to the linked image, the unlinked logo image is inside a `span` tag with the same “custom-logo-link” class.

### Displaying the custom logo in your theme

A custom logo can be displayed in the theme using `` the_`custom_logo()` `` function. But it’s recommended to wrap the code in a `function_exists()` call to maintain backward compatibility with the older versions of WordPress, like this:

```php
if ( function_exists( 'the_custom_logo' ) ) {
	the_custom_logo();
}
```

Generally logos are added to the `header.php` file of the theme, but it can be elsewhere as well.

If you want to get your current logo URL (or use your own markup) instead of the default markup, you can use the following code:

```php
$custom_logo_id = get_theme_mod( 'custom_logo' );
$logo = wp_get_attachment_image_src( $custom_logo_id , 'full' );
if ( has_custom_logo() ) {
	echo '<img src="' . esc_url( $logo[0] ) . '" alt="' . get_bloginfo( 'name' ) . '">';
} else {
	echo '<h1>' . get_bloginfo('name') . '</h1>';
}
```

### Custom logo template tags

To manage displaying a custom logo in the front-end, these three template tags can be used:

*   `[get_custom_logo()](https://developer.wordpress.org/reference/functions/get_custom_logo/) -` Returns markup for a custom logo.
*   `[the_custom_logo()](https://developer.wordpress.org/reference/functions/the_custom_logo/) -` Displays markup for a custom logo.
*   `[has_custom_logo()](https://developer.wordpress.org/reference/functions/has_custom_logo/) -` Returns a boolean true/false, whether a custom logo is set or not.