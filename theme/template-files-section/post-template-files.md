# Post Template Files

There are many [template files](https://developer.wordpress.org/themes/basics/template-files/) that WordPress uses to display the Post [post type](https://developer.wordpress.org/themes/basics/post-types/). Any content dealing with a blog or its posts are within the Post post type.

## Index.php

`index.php` will display Post post types if there is no other template file in place. As stated in many places, every theme must have an `index.php` file to be valid. Many basic themes can get away with just using the `index.php` to display their Post post types, but the use cases given above would justify creating other template files.

Often you will want unique content structure or layout depending on what is being displayed. There are many templates you can use to customize content structure based on the context within the site. The two most notable post template files are `home.php` and `single.php` which display a feed of posts and a single post respectively.

## Home.php

When a static front page is used and the site has a page defined for the blog list the `home.php` file is used for the designated blog list page. Use of this template is encouraged over creating a custom page template because blog pagination on a custom page template will not work properly. If there is no `home.php` in the theme `index.php` will be used instead.

## Single.php

It’s good sense to build as simply as possible in your template structure and not make more templates unless you have real need for them. Therefore, most theme developers don’t create a single-post.php file because single.php is specific enough. For the most part, all themes should have a `single.php`. Below is an example of a `single.php` file from the theme Twenty Fifteen.

```php
<?php
/**
 * The template for displaying all single posts and attachments
 *
 * @package WordPress
 * @subpackage Twenty_Fifteen
 * @since Twenty Fifteen 1.0
 */
 
get_header(); ?>
 
    <div id="primary" class="content-area">
        <main id="main" class="site-main" role="main">
 
        <?php
        // Start the loop.
        while ( have_posts() ) : the_post();
 
            /*
             * Include the post format-specific template for the content. If you want to
             * use this in a child theme, then include a file called called content-___.php
             * (where ___ is the post format) and that will be used instead.
             */
            get_template_part( 'content', get_post_format() );
 
            // If comments are open or we have at least one comment, load up the comment template.
            if ( comments_open() || get_comments_number() ) :
                comments_template();
            endif;
 
            // Previous/next post navigation.
            the_post_navigation( array(
                'next_text' => '<span class="meta-nav" aria-hidden="true">' . __( 'Next', 'twentyfifteen' ) . '</span> ' .
                    '<span class="screen-reader-text">' . __( 'Next post:', 'twentyfifteen' ) . '</span> ' .
                    '<span class="post-title">%title</span>',
                'prev_text' => '<span class="meta-nav" aria-hidden="true">' . __( 'Previous', 'twentyfifteen' ) . '</span> ' .
                    '<span class="screen-reader-text">' . __( 'Previous post:', 'twentyfifteen' ) . '</span> ' .
                    '<span class="post-title">%title</span>',
            ) );
 
        // End the loop.
        endwhile;
        ?>
 
        </main><!-- .site-main -->
    </div><!-- .content-area -->
 
<?php get_footer(); ?>
```

In the code example above you can see the header is pulled in with `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` then there are a two html tags. Next [the Loop](https://developer.wordpress.org/themes/basics/the-loop/) starts and the [template tag](https://developer.wordpress.org/themes/basics/template-tags/) `[get_template_part](https://developer.wordpress.org/reference/functions/get_template_part/)(` `'content'``, get_post_format());` pulls in the appropriate content by determining the post type with `[get_post_format()](https://developer.wordpress.org/reference/functions/get_post_format/)`. Next, [comments](https://developer.wordpress.org/themes/functionality/comments/) are pulled in with the template tag [comments\_template()](https://developer.wordpress.org/reference/functions/comments_template/). Then there is some [pagination](https://developer.wordpress.org/themes/functionality/pagination/). Lastly, the content divs are closed and then footer is pulled in with `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)`.

## Singular.php

WordPress Version 4.3 added `singular.php` that comes in the hierarchy after `single.php` for posts, `page.php` for pages, and the variations of each. This template follows the rules of is\_singular() and is used for a single post, regardless of post type. Themes that used the same code for both of those files (or included one in the other) can now simplify down to the one template.

## Archive.php

Unless a developer includes meta data with permalinks in their templates, the `archive.php` will not be used. Meta data is information tied to the post. For example the date something was posted on, the author, and any [categories, tags, or taxonomies](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) used for the post are all examples of meta data. When a visitor to a website clicks on the meta data, the `archive.php` will render any posts associated with that piece of meta data. For example, if a visitor clicks on the name of an author, the `archive.php` will display all posts by that author.

Commonly, the title of the page being displayed by `archive.php` will be the name of the meta data the user clicked on. So if the user clicked on the Author's name, the page name displaying all the other author's posts will be the Author's name and frequently there might be an additional description about the meta data. Here is a code example from Twenty Fifteen on their `archive.php` file. This snippet is the only piece of code that makes the `archive.php` file different from a `home.php` or `index.php` file.

```php
<header class="page-header">
    <?php
        the_archive_title( '<h1 class="page-title">', '</h1>' );
        the_archive_description( '<div class="taxonomy-description">', '</div>' );
    ?>
</header>
<!-- .page-header -->
```