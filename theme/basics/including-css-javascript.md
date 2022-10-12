# Including CSS &amp; JavaScript

When you’re creating your theme, you may want to create additional stylesheets or JavaScript files. However, remember that a WordPress website will not just have your theme active, it will also be using many different plugins. So that everything works harmoniously, it’s important that theme and plugins load scripts and stylesheets using the standard WordPress method. This will ensure the site remains efficient and that there are no incompatibility issues.

Adding scripts and styles to WordPress is a fairly simple process.   Essentially, you will create a function that will enqueue all of your scripts and styles. When enqueuing a script or stylesheet, WordPress creates a handle and path to find your file and any dependencies it may have (like jQuery) and then you will use a hook that will insert your scripts and stylesheets.

## Enqueuing Scripts and Styles

The proper way to add scripts and styles to your theme is to enqueue them in the `functions.php` files. The `style.css` file is required in all themes, but it may be necessary to add other files to extend the functionality of your theme.

Tip: WordPress includes a number of JavaScript files as part of the software package, including commonly used libraries such as jQuery. Before adding your own JavaScript, [check to see if you can make use of an included library](https://developer.wordpress.org/themes/basics/including-css-javascript/#default-scripts-included-and-registered-by-wordpress).

The basics are:

1.  Enqueue the script or style using `wp_enqueue_script()` or `wp_enqueue_style()`

### Stylesheets

Your CSS stylesheets are used to customize the presentation of your theme. A stylesheet is also the file where information about your theme is stored. For this reason, the `style.css` file is **required in every theme.**

Rather then loading the stylesheet in your `header.php` file, you should load it in using `wp_enqueue_style`. In order to load your main stylesheet, you can enqueue it in `functions.php`

To enqueue `style.css`

wp\_enqueue\_style( 'style', get\_stylesheet\_uri() );

This will look for a stylesheet named “style” and load it.

The basic function for enqueuing a style is:

wp\_enqueue\_style( $handle, $src, $deps, $ver, $media );

You can include these parameters:

*   **$handle** is simply the name of the stylesheet.
*   **$src** is where it is located. The rest of the parameters are optional.
*   **$deps** refers to whether or not this stylesheet is dependent on another stylesheet. If this is set, this stylesheet will not be loaded unless its dependent stylesheet is loaded first.
*   **$ver** sets the version number.
*   **$media** can specify which type of media to load this stylesheet in, such as ‘all’, ‘screen’, ‘print’ or ‘handheld.’

So if you wanted to load a stylesheet named “slider.css” in a folder named “CSS” in you theme’s root directory, you would use:

wp\_enqueue\_style( 'slider', get\_template\_directory\_uri() . '/css/slider.css',false,'1.1','all');

### Scripts

Any additional JavaScript files required by a theme should be loaded using `wp_enqueue_script`. This ensures proper loading and caching, and allows the use conditional tags to target specific pages. These are **optional**.

`wp_enqueue_script` uses a similar syntax to `wp_enqueue_style`.

Enqueue your script:

wp\_enqueue\_script( $handle, $src, $deps, $ver, $in\_footer);

*   **$handle** is the name for the script.
*   **$src** defines where the script is located.
*   **$deps** is an array that can handle any script that your new script depends on, such as jQuery.
*   **$ver** lets you list a version number.
*   **$in\_footer** is a boolean parameter (true/false) that allows you to place your scripts in the footer of your HTML document rather then in the header, so that it does not delay the loading of the DOM tree.

Your enqueue function may look like this:

wp\_enqueue\_script( 'script', get\_template\_directory\_uri() . '/js/script.js', array ( 'jquery' ), 1.1, true);

### The Comment Reply Script

WordPress comments have quite a bit of functionality in them right out of the box, including threaded comments and enhanced comment forms. In order for comments to work properly, they require some JavaScript. However, since there are certain options that need to be defined within this JavaScript, the comment-reply script should be added to every classic theme that uses comments.

**In block themes, the script is included when you place a comment block. You do not need to add it manually.**

The proper way to include comment reply in classic themes is to use conditional tags to check if certain conditions exist, so that the script isn’t being loaded unnecessarily. For instance, you can only load scripts on single post pages using `[is_singular](https://developer.wordpress.org/reference/functions/is_singular/)`, and check to make sure that “Enable threaded comments” is selected by the user. So you can set up a function like:

if ( is\_singular() && comments\_open() && get\_option( 'thread\_comments' ) ) {
    wp\_enqueue\_script( 'comment-reply' );
}

If comments are enabled by the user, and we are on a post page, then the comment reply script will be loaded. Otherwise, it will not.

### Combining Enqueue Functions

It is best to combine all enqueued scripts and styles into a single function, and then call them using the `wp_enqueue_scripts` action. This function and action should be located somewhere below the initial setup (performed above).

function add\_theme\_scripts() {
  wp\_enqueue\_style( 'style', get\_stylesheet\_uri() );
 
  wp\_enqueue\_style( 'slider', get\_template\_directory\_uri() . '/css/slider.css', array(), '1.1', 'all');
 
  wp\_enqueue\_script( 'script', get\_template\_directory\_uri() . '/js/script.js', array ( 'jquery' ), 1.1, true);
 
    if ( is\_singular() && comments\_open() && get\_option( 'thread\_comments' ) ) {
      wp\_enqueue\_script( 'comment-reply' );
    }
}
add\_action( 'wp\_enqueue\_scripts', 'add\_theme\_scripts' );

## Default Scripts Included and Registered by WordPress

By default, WordPress includes many popular scripts commonly used by web developers, as well as the scripts used by WordPress itself. Some of them are listed on this reference page:

> [](https://developer.wordpress.org/reference/functions/wp_enqueue_script/)[wp\_enqueue\_script()](https://developer.wordpress.org/reference/functions/wp_enqueue_script/)

**The list is far from complete.** You can find a full list of included files in [wp-includes/script-loader.php](https://core.trac.wordpress.org/browser/trunk/src/wp-includes/script-loader.php).