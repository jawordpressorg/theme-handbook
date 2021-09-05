# Custom Backgrounds

Custom Backgrounds is a theme feature that provides for customization of the background color and image.  
Theme developer needs 2 steps to implement it.

1.  Enable Custom Background – [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/)
2.  Display Custom Background – [wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) and [body\_class()](https://developer.wordpress.org/reference/functions/body_class/)

## Enable Custom Backgrounds

Use [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) in the `functions.php` file to enable custom backgrounds.

</p>
add\_theme\_support( 'custom-background' );
<p>

You can specify default parameters. In below example using default ‘#0000ff’ background color (blue) with ‘wapuu.jpg’ background image that was stored under the /images folder.

</p>
$args = array(
    'default-color' => '0000ff',
    'default-image' => get\_template\_directory\_uri() . '/images/wapuu.jpg',
);
add\_theme\_support( 'custom-background', $args );
<p>

By calling [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/), Customizer displays ‘Background Image’ menu and ‘Background Color’ section in Colors menu.

## Display Custom Backgrounds

In general, invokes [wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) and [body\_class()](https://developer.wordpress.org/reference/functions/body_class/) in `header.php` file to display the custom backgrounds.

</p>
<!DOCTYPE html>
<html>
<head>
    <?php wp\_head(); ?>
</head>
<body <?php body\_class(); ?>>
<p>

[wp\_head()](https://developer.wordpress.org/reference/functions/wp_head/) generates an extra style sheet in-line with the HTML headers, usually right before the end of the document’s HEAD element. The extra style sheet overrides the background values from the theme’s style sheet.  
In our example, following code will be generated in the HTML. Notice that body tag includes “custom-background ” class.

</p>
<!DOCTYPE html>
<html lang="en-US" class="no-js">

<head>
	...
<style type="text/css" id="custom-background-css">
body.custom-background {
  background-image: url("http://example.com/wordpress/wp-content/themes/my-first-theme/images/wapuu.jpg");
  background-position: left top;
  background-size: auto;
  background-repeat: repeat;
  background-attachment: scroll;
}
</style>
	...
</head>

<body class="home page-template-default page page-id-211 logged-in admin-bar no-customize-support custom-background">

	...
<p>

[Expand full source code](#)[Collapse full source code](#)

Now you’ll see repeated background images

![](https://developer.wordpress.org/files/2017/03/custom_background_1.jpg)

## Another default example

This is another example of default value set.

</p>
$another\_args = array(
    'default-color'      => '0000ff',
    'default-image'      => get\_template\_directory\_uri() . '/images/wapuu.jpg',
    'default-position-x' => 'right',
    'default-position-y' => 'top',
    'default-repeat'     => 'no-repeat',
);
add\_theme\_support( 'custom-background', $another\_args );
<p>

This will show single image at the top right corner as below.

![](https://developer.wordpress.org/files/2017/03/custom_background_2.jpg)

Note: Even if we specified the ‘default-color’ as ‘#0000ff’ (blue), the background color is not blue. Setting the default-image parameter will instantly cause that value to become the effective Custom Background, whereas setting the default-color has no effect. It is just set as default background color in Color menu of Customizer, and enhanced when Administrator save it.

![](https://developer.wordpress.org/files/2017/03/custom_background_3.jpg)