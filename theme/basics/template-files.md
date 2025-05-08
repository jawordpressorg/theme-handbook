# Template Files

Template files are used throughout WordPress themes, but first let’s learn about the terminology.

## Template Terminology

The term “template” is used in different ways when working with WordPress themes:

*   Templates files exist within a theme and express how your site is displayed.
*   [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) is the logic WordPress uses to decide which theme template file(s) to use, depending on the content being requested.
*   [Page Templates](https://developer.wordpress.org/themes/template-files-section/page-template-files/ "Page Templates") are those that apply to pages, posts, and custom post types to change their look and feel.

**In classic themes,** [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") are built-in WordPress functions you can use inside a template file to retrieve and display data (such as [`the_title()`](https://developer.wordpress.org/reference/hooks/the_title/ "Function Reference/the title") and [`the_content()`](https://developer.wordpress.org/reference/hooks/the_content/ "Function Reference/the content")).

**In block themes,** blocks are used instead of template tags.

## Template files

WordPress themes are made up of template files.

*   In classic themes these are PHP files that contain a mixture of HTML, [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags"), and PHP code.
*   In block themes these are HTML files that contain HTML markup representing blocks.

When you are building your theme, you will use template files to affect the layout and design of different parts of your website. For example, you would use a `header` template or template part to create a header.

When someone visits a page on your website, WordPress loads a template based on the request. The type of content that is displayed by the template file is determined by the [Post Type](https://developer.wordpress.org/themes/basics/post-types/) associated with the template file. The [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy") describes which template file WordPress will load based on the type of request and whether the template exists in the theme. The server then parses the code in the template and returns HTML to the visitor.

The most critical template file is `the index`, which is the catch-all template if a more-specific template can not be found in the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/). Although a theme only needs a `index` template, typically themes include numerous templates to display different content types and contexts.

## Template partials

A template part is a piece of a template that is included as a part of another template, such as a site header. Template part can be embedded in multiple templates, simplifying theme creation. Common template parts include:

*   `header.php` or `header.html` for generating the site’s header
*   `footer.php` or `footer.html` for generating the footer
*   `sidebar.php` or `sidebar.html` for generating the sidebar

While the above template files are special-case in WordPress and apply to just one portion of a page, you can create any number of template partials and include them in other template files.

In block themes, template parts must be placed inside a folder called parts.

## Common WordPress template files

Below is a list of some basic theme templates and files recognized by WordPress.

**index.php (classic theme) or index.html (block theme)**

The main template file. It is **required** in all themes.

**style.css**

The main stylesheet. It is **required** in all themes and contains the information header for your theme.

**rtl.css**

The right-to-left stylesheet is included automatically if the website language’s text direction is right-to-left.

**front-page.php (classic theme) or front-page.html (block theme)**

The front page template is always used as the site front page if it exists, regardless of what settings on **Admin > Settings > Reading**.

**home.php (classic theme) or home.html (block theme)**

The home page template is the front page by default. If you do not set WordPress to use a static front page, this template is used to show latest posts.

**singular.php (classic theme) or singular.html (block theme)**

The singular template is used for posts when `single.php` is not found, or for pages when `page.php` are not found. If `singular.php` is not found, `index.php` is used.

**single.php (classic theme) or single.html (block theme)**

The single post template is used when a visitor requests a single post.

**single-{post-type}.php (classic theme) or single-{post-type}.html (block theme)**

The single post template used when a visitor requests a single post from a custom post type. For example, `single-book.php` would be used for displaying single posts from a custom post type named *book*.

**archive-{post-type}.php (classic theme) or archive-{post-type}.html (block theme)**

The archive post type template is used when visitors request a custom post type archive. For example, `archive-books.php` would be used for displaying an archive of posts from the custom post type named *books*. The archive template file is used if the `archive-{post-type} template` is not present.

**page.php (classic theme) or page.html (block theme)**

The page template is used when visitors request individual pages, which are a built-in template.

**page-{slug}.php (classic theme) or page-{slug}.html (block theme)**

The page slug template is used when visitors request a specific page, for example one with the “about” slug (page-about.php).

**category.php (classic theme) or category.html (block theme)**

The category template is used when visitors request posts by category.

**tag.php (classic theme) or tag.html (block theme)**

The tag template is used when visitors request posts by tag.

**taxonomy.php (classic theme) or taxonomy.html (block theme)**

The taxonomy term template is used when a visitor requests a term in a custom taxonomy.

**author.php (classic theme) or author.html (block theme)**

The author page template is used whenever a visitor loads an author page.

**date.php (classic theme) or date.html (block theme)**

The date/time template is used when posts are requested by date or time. For example, the pages generated with these slugs:  
http://example.com/blog/2014/  
http://example.com/blog/2014/05/  
http://example.com/blog/2014/05/26/

**archive.php (classic theme) or archive.html (block theme)**

The archive template is used when visitors request posts by category, author, or date. **Note**: this template will be overridden if more specific templates are present like `category.php`, `author.php`, and `date.php`.

**search.php (classic theme) or search.html (block theme)**

The search results template is used to display a visitor’s search results.

**attachment.php (classic theme) or attachment.html (block theme)**

The attachment template is used when viewing a single attachment like an image, pdf, or other media file.

**image.php (classic theme) or image.html (block theme)**

The image attachment template is a more specific version of `attachment.php` and is used when viewing a single image attachment. If not present, WordPress will use `attachment.php` instead.

**404.php (classic theme) or 404.html (block theme)**

The 404 template is used when WordPress cannot find a post, page, or other content that matches the visitor’s request.

**comments.php**

The comments template in classic themes. In block themes, blocks are used instead.

## Using template files

### Classic themes

In classic themes, within WordPress templates, you can use [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") to display information dynamically, include other template files, or otherwise customize your site.

For example, in your `index.php` you can include other files in your final generated page:

*   To include the header, use [get\_header()](https://developer.wordpress.org/reference/functions/get_header/ "Function Reference/get header")
*   To include the sidebar, use [get\_sidebar()](https://developer.wordpress.org/reference/functions/get_sidebar/ "Function Reference/get sidebar")
*   To include the footer, use [get\_footer()](https://developer.wordpress.org/reference/functions/get_footer/ "Function Reference/get footer")
*   To include the search form, use [get\_search\_form()](https://developer.wordpress.org/reference/functions/get_search_form/ "Function Reference/get search form")
*   To include custom theme files, use [get\_template\_part()](https://developer.wordpress.org/reference/functions/get_template_part/ "Function Reference/get template part")

Here is an example of WordPress template tags to *include* specific templates into your page:

```php
<?php get_sidebar(); ?>
<?php get_template_part( 'featured-content' ); ?>
<?php get_footer(); ?>
```

There’s an entire page on [Template Tags](https://developer.wordpress.org/themes/basics/template-tags/ "Template Tags") that you can dive into to learn all about them.

Refer to the section [Linking Theme Files & Directories](https://developer.wordpress.org/themes/basics/linking-theme-files-directories/ "Linking Theme Files & Directories") for more information on linking component templates.

### Block themes

In block themes you use blocks instead of template tags. Block markup is the HTML code that WordPress uses to display the block. Template parts are blocks, and you add them to your template files the same way as you add blocks.

To include a header or footer template part, add the block markup for the template part. The `slug` is the name of the part. If the file you want to include is called `header.html`, then the slug is “header”:

```markup
<!-- wp:template-part {"slug":"header"} /-->
(your page content)
<!-- wp:template-part {"slug":"footer"} /-->
```

To include the search form, use the block markup for the search block:

```markup
<!-- wp:search {"label":"Search","buttonText":"Search"} /-->
```