# Custom Post Type Template Files

The WordPress theme system supports custom [templates](https://developer.wordpress.org/themes/basics/template-files/) for custom post types. Custom templates for the single display of posts belonging to custom post types have been supported since WordPress [Version 3.0](https://codex.wordpress.org/Version_3.0) and the support for custom templates for archive displays was added in [Version 3.1](https://codex.wordpress.org/Version_3.1).

## Custom Post Type – Template Hierarchy

WordPress will work through the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) and use the template file it comes across first. So if you want to create a custom template for your `acme_product` custom post type, a good place to start is by copying the `single.php` file, saving it as `single-acme_product.php` and editing that.

However if you don’t want to create custom template files, WordPress will use the files already present in your theme, which would be `archive.php` and `single.php` and `index.php` files.

Single posts and their archives can be displayed using the `single.php` and `archive.php` template files respectively,

*   single posts of a custom post type will use **single-{post\_type}.php**
*   and their archives will use **archive-{post\_type}.php**
*   and if you don’t have this post type archive page you can pass **BLOG\_URL?post\_type={post\_type}**

where `{post_type}` is the `$post_type` argument of the [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/) function.

So for the above example, you could create `single-acme_product.php` and `archive-acme_product.php` template files for single product posts and their archives.

Alternatively, you can use the `is_post_type_archive()` function in any template file to check if the query shows an archive page of a given post types(s), and the `post_type_archive_title()` to display the post type title.

## Custom Post Type templates

*   **single-{post-type}.php**  
    The single post template used when a visitor requests a single post from a custom post type. For example, `single-acme_product.php` would be used for displaying single posts from a custom post type named `acme_product`.
*   **archive-{post-type}.php**  
    The archive post type template is used when visitors request a custom post type archive. For example, `archive-acme_product.php` would be used for displaying an archive of posts from the custom post type named `acme_product`. The `archive.php` template file is used if the `archive-{post-type}.php` is not present.
*   **index.php**  
    The `index.php` is used if a specific query template (`single-{post-type}.php, single.php, archive-{post-type}.php, archive.php, search.php`) for the custom post type is not present.

## Function Reference

*   [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/) : Registers a post type.
*   [is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/) : Checks if the query for an existing post type archive page.
*   [post\_type\_archive\_title()](https://developer.wordpress.org/reference/functions/post_type_archive_title/) : Display or retrieve title for a post type archive.