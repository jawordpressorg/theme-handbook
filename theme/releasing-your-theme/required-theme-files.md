# Required Theme Files

  
**Block theme:** See [Create a Block Theme](https://developer.wordpress.org/block-editor/how-to-guides/themes/create-block-theme/) for building a block theme  

Classic themes must  include the required theme files. These files must follow template file standards set by the themes team. For Classic themes, additional standard template files are recommended to use. Learn more about the [Organizing Theme Files](https://developer.wordpress.org/themes/basics/organizing-theme-files/).

## Classic Themes Required Theme Files

1.  **style.css  
    **Your theme’s main [stylesheet](https://developer.wordpress.org/themes/basics/including-css-javascript/) file. This file will also include information about your theme, such as author name, version number, and plugin URL, in it’s header.
2.  **index.php  
    **The main [template](https://developer.wordpress.org/themes/basics/template-files/) file for your theme. This will be the template for the homepage on your site unless a static front page is specified. If you *only* include this template file, it must include all functionality of your theme. However, you can use as many relevant template files as you want in your theme.
3.  ****comments.php  
    ****The comment template which is included wherever comments are allowed. This file should provide support for threaded comments and trackbacks, and should style author comments differently then user comments. See the [Comments](https://developer.wordpress.org/themes/functionality/comments/) page for more information.
4.  **screenshot  
    **In the WordPress.org theme directory, the screenshot acts as a visual indicator of what your theme looks like. It is visible both in the web view and in the admin dashboard. The screenshot must not be bigger than 1200 x 900px. 

While these files are the only files required by the theme review team for acceptance into the WordPress.org theme directory, you may use other template files. Of course, any file mentioned in the tutorial in this handbook may be used in your theme.