# Featured Images &amp; Post Thumbnails

Featured images (also sometimes called Post Thumbnails) are images that represent an individual Post, Page, or Custom Post Type. When you create your Theme, you can output the featured image in a number of different ways, on your archive page, in your header, or above a post, for example.

## Enabling Support for Featured Image

Themes must declare support for the Featured Image function before the Featured Image interface will appear on the Edit screen. Support is declared by putting the following in your theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/theme-basics/theme-functions/ "Theme Functions") file:

```php
add_theme_support( 'post-thumbnails' );
```

To enable Featured Image only for specific post types, see [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/ "Allows a theme to register its support of a certain feature...")

## Setting a Featured Image

Once you add support for Featured Images, the Featured Image meta box will be visible on the appropriate content item’s Edit screens. If a user is unable to see it, they can enable it in their screen options.

By default, the Featured Image meta box is displayed in the sidebar of the Edit Post and Edit Page screens.

[![devhbook-featured_image](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)](https://i0.wp.com/make.wordpress.org/docs/files/2013/02/devhbook-featured_image1.png?ssl=1)

## Function Reference

`[add_image_size()](https://developer.wordpress.org/reference/functions/add_image_size/ "Register a new image size")` – Register a new image size.  
`[set_post_thumbnail_size()](https://developer.wordpress.org/reference/functions/set_post_thumbnail_size/ "Registers an image size for the post thumbnail")` – Registers an image size for the post thumbnail.

`[has_post_thumbnail()](https://developer.wordpress.org/reference/functions/has_post_thumbnail/ "Check if post has an image attached")` – Check if post has an image attached.  
`[the_post_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail")` – Display Post Thumbnail.

`[get_the_post_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")` – Retrieve Post Thumbnail.  
`[get_post_thumbnail_id()](https://developer.wordpress.org/reference/functions/get_post_thumbnail_id/ "Retrieve Post Thumbnail ID")` – Retrieve Post Thumbnail ID.

## Image Sizes

The default image sizes of WordPress are “Thumbnail”, “Medium”, “Large” and “Full Size” (the original size of the image you uploaded). These image sizes can be configured in the WordPress Administration Media panel under **\>Settings > Media**. You can also define your own image size by passing an array with your image dimensions:

```php
the_post_thumbnail(); // Without parameter ->; Thumbnail
the_post_thumbnail( 'thumbnail' ); // Thumbnail (default 150px x 150px max)
the_post_thumbnail( 'medium' ); // Medium resolution (default 300px x 300px max)
the_post_thumbnail( 'medium_large' ); // Medium-large resolution (default 768px x no height limit max)
the_post_thumbnail( 'large' ); // Large resolution (default 1024px x 1024px max)
the_post_thumbnail( 'full' ); // Original image resolution (unmodified)
the_post_thumbnail( array( 100, 100 ) ); // Other resolutions (height, width)
```

## Add Custom Featured Image Sizes

In addition to defining image sizes individually using

```php
the_post_thumbnail( array(  ,  ) );
```

you can create custom featured image sizes in your theme’s functions file that can then be called in your theme’s template files.

```php
add_image_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)
```

Here is an example of how to create custom Featured Image sizes in your theme’s `functions.php` file.

```php
if ( function_exists( 'add_theme_support' ) ) {
    add_theme_support( 'post-thumbnails' );
    set_post_thumbnail_size( 150, 150, true ); // default Featured Image dimensions (cropped)

    // additional image sizes
    // delete the next line if you do not need additional image sizes
    add_image_size( 'category-thumb', 300, 9999 ); // 300 pixels wide (and unlimited height)
}
```

## Set the Featured Image Output Size

To be used in the current Theme’s functions.php file.  
You can use `set_post_thumbnail_size()` to set the default Featured Image size by resizing the image proportionally (that is, without distorting it):

```php
set_post_thumbnail_size( 50, 50 ); // 50 pixels wide by 50 pixels tall, resize mode
```

Set the default Featured Image size by cropping the image (either from the sides, or from the top and bottom):

```php
set_post_thumbnail_size( 50, 50, true ); // 50 pixels wide by 50 pixels tall, crop mode
```

## Styling Featured Images

Featured Images are given a class “wp-post-image”. They also get a class depending on the size of the thumbnail being displayed. You can style the output with these CSS selectors:

```css
img.wp-post-image
img.attachment-thumbnail
img.attachment-medium
img.attachment-large
img.attachment-full
```

You can also give Featured Images their own classes by using the attribute parameter in [the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/the_post_thumbnail/ "Display Post Thumbnail").  
Display the Featured Image with a class “alignleft”:

```php
the_post_thumbnail( 'thumbnail', array( 'class' => 'alignleft' ) );
```

## Examples

### Default Usage

```php
// check if the post or page has a Featured Image assigned to it.
if ( has_post_thumbnail() ) {
    the_post_thumbnail();
}
```

To return the Featured Image for use in your PHP code instead of displaying it, use: [get\_the\_post\_thumbnail()](https://developer.wordpress.org/reference/functions/get_the_post_thumbnail/ "Retrieve Post Thumbnail")

```php
// check for a Featured Image and then assign it to a PHP variable for later use
if ( has_post_thumbnail() ) {
    $featured_image = get_the_post_thumbnail();
}
```

### Linking to Post Permalink or Larger Image

Don’t use these two examples together in the same Theme.

Example 1. To link Post Thumbnails to the Post Permalink in a specific loop, use the following within your Theme’s template files:

```php
<?php if ( has_post_thumbnail()) : ?>
    <a href="<?php the_permalink(); ?>" alt="<?php the_title_attribute(); ?>">
        <?php the_post_thumbnail(); ?>
    </a>
<?php endif; ?>
```

Example 2. To link **all Post Thumbnails** on your website to the Post Permalink, put this in the current Theme’s [functions.php](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/theme-functions/ "Theme Functions") file:

```php
add_filter( 'post_thumbnail_html', 'my_post_image_html', 10, 3 );
function my_post_image_html( $html, $post_id, $post_image_id ) {

  $html = '<a href="' . get_permalink( $post_id ) . '">' . $html . '</a>';
  return $html;

}
```

This example links to the “large” Post Thumbnail image size and must be used within The Loop.

```php
if ( has_post_thumbnail()) {
    $large_image_url = wp_get_attachment_image_src( get_post_thumbnail_id(), 'large');
    echo '<a href="' . $large_image_url[0] . '">';
    the_post_thumbnail('thumbnail');
    echo '</a>';
}
```

## Source File

*   [wp-includes/post-thumbnail-template.php](https://core.trac.wordpress.org/browser/tags/3.5.1/wp-includes/post-thumbnail-template.php#L0)

## External Resources

*   [Everything you need to know about WordPress 2.9’s post image feature](http://justintadlock.com/archives/2009/11/16/everything-you-need-to-know-about-wordpress-2-9s-post-image-feature)
*   [The Ultimative Guide For the\_post\_thumbnail In WordPress 2.9](http://wpengineer.com/the-ultimative-guide-for-the_post_thumbnail-in-wordpress-2-9/)
*   [New in WordPress 2.9: Post Thumbnail Images](http://markjaquith.wordpress.com/2009/12/23/new-in-wordpress-2-9-post-thumbnail-images/)