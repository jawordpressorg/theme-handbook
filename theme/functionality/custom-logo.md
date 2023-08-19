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