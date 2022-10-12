# Custom Headers

## Custom Header

[Custom headers](https://developer.wordpress.org/themes/functionality/custom-headers/) allow site owners to upload their own “title” image to their site, which can be placed at the top of certain pages. These can be customized and cropped by the user through a visual editor in the **Appearance > Header** section of the admin panel. You may also place text beneath or on top of the header. To support fluid layouts and responsive design, these headers may also be flexible. Headers are placed into a theme using `get_custom_header()`, but they must first be added to your *functions.php* file using `add_theme_support()`. Custom headers are **optional.**

To set up a basic, flexible, custom header with text you would include the following code:

function themename\_custom\_header\_setup() {
    $args = array(
        'default-image'      => get\_template\_directory\_uri() . 'img/default-image.jpg',
        'default-text-color' => '000',
        'width'              => 1000,
        'height'             => 250,
        'flex-width'         => true,
        'flex-height'        => true,
    );
    add\_theme\_support( 'custom-header', $args );
}
add\_action( 'after\_setup\_theme', 'themename\_custom\_header\_setup' );

 *The [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that custom headers are registered after the theme is loaded.*

### What are Custom Headers?

When you enable Custom Headers in your theme, users can change their header image using the WordPress theme Customizer. This gives users more control and flexibility over the look of their site.

## Add Custom Header Support to your Theme

To enable Custom Headers in your theme, add the following to your *`functions.php`* file:

add\_theme\_support( 'custom-header' );

When enabling Custom Headers, you can configure several other options by passing along arguments to the `add_theme_support()` function.

You can pass specific configuration options to the `add_theme_support` function using an array:

function themename\_custom\_header\_setup() {
    $defaults = array(
        // Default Header Image to display
        'default-image'         => get\_template\_directory\_uri() . '/images/headers/default.jpg',
        // Display the header text along with the image
        'header-text'           => false,
        // Header text color default
        'default-text-color'        => '000',
        // Header image width (in pixels)
        'width'             => 1000,
        // Header image height (in pixels)
        'height'            => 198,
        // Header image random rotation default
        'random-default'        => false,
        // Enable upload of image file in admin 
        'uploads'       => false,
        // function to be called in theme head section
        'wp-head-callback'      => 'wphead\_cb',
        //  function to be called in preview page head section
        'admin-head-callback'       => 'adminhead\_cb',
        // function to produce preview markup in the admin screen
        'admin-preview-callback'    => 'adminpreview\_cb',
        );
}
add\_action( 'after\_setup\_theme', 'themename\_custom\_header\_setup' );

### Flexible Header Image

If flex-height or flex-width are not included in the array, height and width will be fixed sizes. If flex-height and flex-width are included, height and width will be used as suggested dimensions instead.

### Header text

By default, the user will have the option of whether or not to display header text over the image. There is no option to force the header text on the user, but if you want to remove the header text completely, you can set ‘header-text’ to ‘false’ in the arguments. This will remove the header text and the option to toggle it.

## Examples

### Set a custom header image

When the user first installs your theme, you can include a default header that will be selected before they choose their own header. This allows users to set up your theme more quickly and use your default image until they’re ready to upload their own.

Set a default header image 980px width and 60px height:

$header\_info = array(
    'width'         => 980,
    'height'        => 60,
    'default-image' => get\_template\_directory\_uri() . '/images/sunset.jpg',
);
add\_theme\_support( 'custom-header', $header\_info );
 
$header\_images = array(
    'sunset' => array(
            'url'           => get\_template\_directory\_uri() . '/images/sunset.jpg',
            'thumbnail\_url' => get\_template\_directory\_uri() . '/images/sunset\_thumbnail.jpg',
            'description'   => 'Sunset',
    ),
    'flower' => array(
            'url'           => get\_template\_directory\_uri() . '/images/flower.jpg',
            'thumbnail\_url' => get\_template\_directory\_uri() . '/images/flower\_thumbnail.jpg',
            'description'   => 'Flower',
    ),  
);
register\_default\_headers( $header\_images );

![](https://developer.wordpress.org/files/2014/10/custom_headers_example1.jpg)

Do not forget to call [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) to register a default image. In this example, `sunset.jpg` is the default image and `flower.jpg` is an alternative selection in Customizer.

From Administration Screen, Click **Appearance > Header** to display Header Image menu in Customizer. Notice that width and height specified in [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) is displayed as recommended size, and `flower.jpg` is shown as selectable option.

### Use flexible headers

By default, the user will have to crop any images they upload to fit in the width and height you specify. However, you can let users upload images of any height and width by specifying ‘flex-width’ and ‘flex-height’ as true. This will let the user skip the cropping step when they upload a new photo.

Set flexible headers:

$args = array(
    'flex-width'    => true,
    'width'         => 980,
    'flex-height'   => true,
    'height'        => 200,
    'default-image' => get\_template\_directory\_uri() . '/images/header.jpg',
);
add\_theme\_support( 'custom-header', $args );

update your `header.php` file to:

<img alt="" src="<?php header\_image(); ?>" width="<?php echo absint( get\_custom\_header()->width ); ?>" height="<?php echo absint( get\_custom\_header()->height ); ?>">

### Displaying Custom Header

To display the custom header, function [get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) retrieves the header image. [get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) gets the custom header data.  
E.g. below shows how custom header images can be used to display the header in the theme. The below code goes into header.php file.

<?php if ( get\_header\_image() ) : ?>
    <div id="site-header">
        <a href="<?php echo esc\_url( home\_url( '/' ) ); ?>" rel="home">
            <img src="<?php header\_image(); ?>" width="<?php echo absint( get\_custom\_header()->width ); ?>" height="<?php echo absint( get\_custom\_header()->height ); ?>" alt="<?php echo esc\_attr( get\_bloginfo( 'name', 'display' ) ); ?>">
        </a>
    </div>
<?php endif; ?>

### Backwards Compatibility

Custom Headers are supported in WordPress 3.4 and above. If you’d like your theme to support WordPress installations that are older than 3.4, you can use the following code instead of `add_theme_support( ‘custom-header’);`

global $wp\_version;
if ( version\_compare( $wp\_version, '3.4', '>=' ) ) :
    add\_theme\_support( 'custom-header' );
else :
    add\_custom\_image\_header( $wp\_head\_callback, $admin\_head\_callback );
endif;

## Function Reference

*   [](https://developer.wordpress.org/reference/functions/header_image/)[header\_image()](https://developer.wordpress.org/reference/functions/header_image/) Display header image URL.
*   [](https://developer.wordpress.org/reference/functions/get_header_image/)[get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) Retrieve header image for custom header.
*   [](https://developer.wordpress.org/reference/functions/get_custom_header/)[get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) Get the header image data.
*   [](https://developer.wordpress.org/reference/functions/get_random_header_image/)[get\_random\_header\_image()](https://developer.wordpress.org/reference/functions/get_random_header_image/) Retrieve header image for custom header.
*   [](https://developer.wordpress.org/reference/functions/add_theme_support/)[add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) Registers theme support for a given feature.
*   [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) Registers a selection of default headers to be displayed by the Customizer.