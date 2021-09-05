# Featured Images &amp; Post Thumbnails

Featured images (also sometimes called Post Thumbnails) are images that represent an individual Post, Page, or Custom Post Type. When you create your Theme, you can output the featured image in a number of different ways, on your archive page, in your header, or above a post, for example.

## Enabling Support for Featured Image

Themes must declare support for the Featured Image function before the Featured Image interface will appear on the Edit screen. Support is declared by putting the following in your theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/theme-basics/theme-functions/ "Theme Functions") file:

add\_theme\_support( 'post-thumbnails' );

Note: To enable Featured Image only for specific post types, see [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/ "Allows a theme to register its support of a certain feature...")

## Setting a Featured Image

Once you add support for Featured Images, the Featured Image meta box will be visible on the appropriate content item’s Edit screens. If a user is unable to see it, they can enable it in their screen options.

By default, the Featured Image meta box is displayed in the sidebar of the Edit Post and Edit Page screens.

[![devhbook-featured_image](https://make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png)](https://make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png)

## Function Reference

`[add_image_size()](https://developer.wordpress.org/reference/functions/add_image_size/ "Register a new image size")`– Register a new image size…  
`[set_post_thumbnail_size()](https://developer.wordpress.org/reference/functions/set_post_thumbnail_size/ "Registers an image size for the post thumbnail")` – Registers an image size for the post thumbnail…

`[has_post_thumbnail()](https://developer.wordpress.org/reference/functions/has_post_thumbnail/ "Check if post has an image attached")` – Check if post has an image attached…  
`[the_post_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail")` – Display Post Thumbnail…

`[get_the_post_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")` – Retrieve Post Thumbnail…  
`[get_post_thumbnail_id()](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id/ "Retrieve Post Thumbnail ID")` – Retrieve Post Thumbnail ID…

## Image Sizes

The default image sizes of WordPress are “Thumbnail”, “Medium”, “Large” and “Full Size” (the original size of the image you uploaded). These image sizes can be configured in the WordPress Administration Media panel under **\>Settings > Media**. You can also define your own image size by passing an array with your image dimensions:

<br />
the\_post\_thumbnail(); // Without parameter ->; Thumbnail<br />
the\_post\_thumbnail( 'thumbnail' ); // Thumbnail (default 150px x 150px max)<br />
the\_post\_thumbnail( 'medium' ); // Medium resolution (default 300px x 300px max)<br />
the\_post\_thumbnail( 'medium\_large' ); // Medium-large resolution (default 768px x no height limit max)<br />
the\_post\_thumbnail( 'large' ); // Large resolution (default 1024px x 1024px max)<br />
the\_post\_thumbnail( 'full' ); // Original image resolution (unmodified)<br />
the\_post\_thumbnail( array( 100, 100 ) ); // Other resolutions (height, width)<br />

## Add Custom Featured Image Sizes

In addition to defining image sizes individually using

the\_post\_thumbnail( array(  ,  ) );

you can create custom featured image sizes in your theme’s functions file that can then be called in your theme’s template files.

add\_image\_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)

Here is an example of how to create custom Featured Image sizes in your theme’s `functions.php` file.

if ( function\_exists( 'add\_theme\_support' ) ) {<br />
    add\_theme\_support( 'post-thumbnails' );<br />
    set\_post\_thumbnail\_size( 150, 150, true ); // default Featured Image dimensions (cropped)</p>
<p>    // additional image sizes<br />
    // delete the next line if you do not need additional image sizes<br />
    add\_image\_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)<br />
 }

## Set the Featured Image Output Size

To be used in the current Theme’s functions.php file.  
You can use `set_post_thumbnail_size()` to set the default Featured Image size by resizing the image proportionally (that is, without distorting it):

set\_post\_thumbnail\_size( 50, 50 ); // 50 pixels wide by 50 pixels tall, resize mode

Set the default Featured Image size by cropping the image (either from the sides, or from the top and bottom):

set\_post\_thumbnail\_size( 50, 50, true ); // 50 pixels wide by 50 pixels tall, crop mode

## Styling Featured Images

Featured Images are given a class “wp-post-image”. They also get a class depending on the size of the thumbnail being displayed. You can style the output with these CSS selectors:

img.wp-post-image<br />
img.attachment-thumbnail<br />
img.attachment-medium<br />
img.attachment-large<br />
img.attachment-full

You can also give Featured Images their own classes by using the attribute parameter in [the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail").  
Display the Featured Image with a class “alignleft”:

the\_post\_thumbnail( 'thumbnail', array( 'class' => 'alignleft' ) );

## Examples

### Default Usage

// check if the post or page has a Featured Image assigned to it.<br />
if ( has\_post\_thumbnail() ) {<br />
    the\_post\_thumbnail();<br />
}<br />

Note: To return the Featured Image for use in your PHP code instead of displaying it, use: [get\_the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")

// check for a Featured Image and then assign it to a PHP variable for later use<br />
if ( has\_post\_thumbnail() ) {<br />
    $featured\_image = get\_the\_post\_thumbnail();<br />
}

### Linking to Post Permalink or Larger Image

Alert: Don’t use these two examples together in the same Theme.

Example 1. To link Post Thumbnails to the Post Permalink in a specific loop, use the following within your Theme’s template files:

<?php if ( has\_post\_thumbnail()) : ?>
    <a href="<?php the\_permalink(); ?>" alt="<?php the\_title\_attribute(); ?>">
        <?php the\_post\_thumbnail(); ?>
    </a>
<?php endif; ?>

Example 2. To link **all Post Thumbnails** on your website to the Post Permalink, put this in the current Theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/theme-functions/ "Theme Functions") file:

<br />
add\_filter( 'post\_thumbnail\_html', 'my\_post\_image\_html', 10, 3 );</p>
<p>function my\_post\_image\_html( $html, $post\_id, $post\_image\_id ) {</p>
<p>  $html = '<a href="' . get\_permalink( $post\_id ) . '">' . $html . '</a>';<br />
  return $html;</p>
<p>}<br />

This example links to the “large” Post Thumbnail image size and must be used within The Loop.

<br />
 if ( has\_post\_thumbnail()) {<br />
    $large\_image\_url = wp\_get\_attachment\_image\_src( get\_post\_thumbnail\_id(), 'large');<br />
    echo '<a href="' . $large\_image\_url&#91;0&#93; . '">';<br />
    the\_post\_thumbnail('thumbnail');<br />
    echo '</a>';<br />
 }<br />

## Source File

*   [wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/tags/3.5.1/wp-includes/post-thumbnail-template.php#L0)

## External Resources

*   [Everything you need to know about WordPress 2.9’s post image feature](http://justintadlock.com/archives/2009/11/16/everything-you-need-to-know-about-wordpress-2-9s-post-image-feature)
*   [The Ultimative Guide For the\_post\_thumbnail In WordPress 2.9](http://wpengineer.com/the-ultimative-guide-for-the_post_thumbnail-in-wordpress-2-9/)
*   [New in WordPress 2.9: Post Thumbnail Images](http://markjaquith.wordpress.com/2009/12/23/new-in-wordpress-2-9-post-thumbnail-images/)