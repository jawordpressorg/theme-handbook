# Custom Headers

## Custom Header

[Custom headers](https://developer.wordpress.org/themes/functionality/custom-headers/ "Custom Headers") allow site owners to upload their own “title” image to their site, which can be placed at the top of certain pages. These can be customized and cropped by the user through a visual editor in the **Appearance > Header** section of the admin panel. You may also place text beneath or on top of the header. To support fluid layouts and responsive design, these headers may also be flexible. Headers are placed into a theme using `get_custom_header()`, but they must first be added to your *functions.php* file using `add_theme_support()`. Custom headers are **optional.**

To set up a basic, flexible, custom header with text you would include the following code:

<br />
function themename\_custom\_header\_setup() {<br />
    $args = array(<br />
        'default-image'      => get\_template\_directory\_uri() . 'img/default-image.jpg',<br />
        'default-text-color' => '000',<br />
        'width'              => 1000,<br />
        'height'             => 250,<br />
        'flex-width'         => true,<br />
        'flex-height'        => true,<br />
    )<br />
    add\_theme\_support( 'custom-header', $args );<br />
}<br />
add\_action( 'after\_setup\_theme', 'themename\_custom\_header\_setup' );<br />

 *The [`after_setup_theme`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that custom headers are registered after the theme is loaded.*

### What are Custom Headers?

When you enable Custom Headers in your theme, users can change their header image using the WordPress theme Customizer. This gives users more control and flexibility over the look of their site.

## Add Custom Header Support to your Theme

To enable Custom Headers in your theme, add the following to your *`functions.php`* file:

<br />
add\_theme\_support( 'custom-header' );<br />

When enabling Custom Headers, you can configure several other options by passing along arguments to the `add_theme_support()` function.

You can pass specific configuration options to the `add_theme_support` function using an array:

<br />
function themename\_custom\_header\_setup() {<br />
	$defaults = array(<br />
		// Default Header Image to display<br />
		'default-image'			=> get\_template\_directory\_uri() . '/images/headers/default.jpg',<br />
		// Display the header text along with the image<br />
		'header-text'			=> false,<br />
		// Header text color default<br />
		'default-text-color'		=> '000',<br />
		// Header image width (in pixels)<br />
		'width'				=> 1000,<br />
		// Header image height (in pixels)<br />
		'height'			=> 198,<br />
		// Header image random rotation default<br />
		'random-default'		=> false,<br />
		// Enable upload of image file in admin<br />
		'uploads'		=> false,<br />
		// function to be called in theme head section<br />
		'wp-head-callback'		=> 'wphead\_cb',<br />
		//  function to be called in preview page head section<br />
		'admin-head-callback'		=> 'adminhead\_cb',<br />
		// function to produce preview markup in the admin screen<br />
		'admin-preview-callback'	=> 'adminpreview\_cb',<br />
		);<br />
}<br />
add\_action( 'after\_setup\_theme', 'themename\_custom\_header\_setup' );<br />

[Expand full source code](#)[Collapse full source code](#)

### Flexible Header Image

If flex-height or flex-width are not included in the array, height and width will be fixed sizes. If flex-height and flex-width are included, height and width will be used as suggested dimensions instead.

### Header text

By default, the user will have the option of whether or not to display header text over the image. There is no option to force the header text on the user, but if you want to remove the header text completely, you can set ‘header-text’ to ‘false’ in the arguments. This will remove the header text and the option to toggle it.

## Examples

### Set a custom header image

When the user first installs your theme, you can include a default header that will be selected before they choose their own header. This allows users to set up your theme more quickly and use your default image until they’re ready to upload their own.

Set a default header image 980px width and 60px height:

<br />
$header\_info = array(<br />
    'width'         => 980,<br />
    'height'        => 60,<br />
    'default-image' => get\_template\_directory\_uri() . '/images/sunset.jpg',<br />
);<br />
add\_theme\_support( 'custom-header', $header\_info );</p>
<p>$header\_images = array(<br />
	'sunset' => array(<br />
			'url'           => get\_template\_directory\_uri() . '/images/sunset.jpg',<br />
			'thumbnail\_url' => get\_template\_directory\_uri() . '/images/sunset\_thumbnail.jpg',<br />
			'description'	=> 'Sunset',<br />
	),<br />
	'flower' => array(<br />
			'url'           => get\_template\_directory\_uri() . '/images/flower.jpg',<br />
			'thumbnail\_url' => get\_template\_directory\_uri() . '/images/flower\_thumbnail.jpg',<br />
			'description'	=> 'Flower',<br />
	),<br />
);<br />
register\_default\_headers( $header\_images );<br />

[Expand full source code](#)[Collapse full source code](#)

![](https://developer.wordpress.org/files/2014/10/custom_headers_example1.jpg)

Do not forget to call [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) to register a default image. In this example, `sunset.jpg` is the default image and `flower.jpg` is an alternative selection in Customizer.

From Administration Screen, Click **Appearance > Header** to display Header Image menu in Customizer. Notice that width and height specified in [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) is displayed as recommended size, and `flower.jpg` is shown as selectable option.

### Use flexible headers

By default, the user will have to crop any images they upload to fit in the width and height you specify. However, you can let users upload images of any height and width by specifying ‘flex-width’ and ‘flex-height’ as true. This will let the user skip the cropping step when they upload a new photo.

Set flexible headers:

<br />
$args = array(<br />
	'flex-width'    => true,<br />
	'width'         => 980,<br />
	'flex-height'   => true,<br />
	'height'        => 200,<br />
	'default-image' => get\_template\_directory\_uri() . '/images/header.jpg',<br />
);<br />
add\_theme\_support( 'custom-header', $args );<br />

update your `header.php` file to:

<br />
&lt;img alt=&quot;&quot; src=&quot;&lt;?php header\_image(); ?>&quot; width=&quot;&lt;?php echo absint( get\_custom\_header()->width ); ?>&quot; height=&quot;&lt;?php echo absint( get\_custom\_header()->height ); ?>&quot;><br />

### Displaying Custom Header

To display the custom header, function [get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) retrives the header image. [get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) gets the custom header data.  
E.g. below shows how custom header images can be used to display the header in the theme. The below code goes into header.php file.

<br />
&lt;?php if ( get\_header\_image() ) : ?><br />
	&lt;div id=&quot;site-header&quot;><br />
		&lt;a href=&quot;&lt;?php echo esc\_url( home\_url( '/' ) ); ?>&quot; rel=&quot;home&quot;><br />
			&lt;img src=&quot;&lt;?php header\_image(); ?>&quot; width=&quot;&lt;?php echo absint( get\_custom\_header()->width ); ?>&quot; height=&quot;&lt;?php echo absint( get\_custom\_header()->height ); ?>&quot; alt=&quot;&lt;?php echo esc\_attr( get\_bloginfo( 'name', 'display' ) ); ?>&quot;><br />
		&lt;/a><br />
	&lt;/div><br />
&lt;?php endif; ?><br />

### Backwards Compatibility

Custom Headers are supported in WordPress 3.4 and above. If you’d like your theme to support WordPress installations that are older than 3.4, you can use the following code instead of `add_theme_support( ‘custom-header’);`

<br />
global $wp\_version;<br />
if ( version\_compare( $wp\_version, '3.4', '>=' ) ) :<br />
	add\_theme\_support( 'custom-header' );<br />
else :<br />
	add\_custom\_image\_header( $wp\_head\_callback, $admin\_head\_callback );<br />
endif;<br />

## Function Reference

*   [header\_image()](https://developer.wordpress.org/reference/functions/header_image/) Display header image URL.
*   [get\_header\_image()](https://developer.wordpress.org/reference/functions/get_header_image/) Retrieve header image for custom header.
*   [get\_custom\_header()](https://developer.wordpress.org/reference/functions/get_custom_header/) Get the header image data.
*   [get\_random\_header\_image()](https://developer.wordpress.org/reference/functions/get_random_header_image/) Retrieve header image for custom header.
*   [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) Registers theme support for a given feature.
*   [register\_default\_headers()](https://developer.wordpress.org/reference/functions/register_default_headers/) Registers a selection of default headers to be displayed by the Customizer.