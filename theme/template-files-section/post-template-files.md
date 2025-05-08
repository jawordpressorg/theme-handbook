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

WordPress Version 4.3 added `singular.php` that comes in the hierarchy after `single.php` for posts, `page.php` for pages, and the variations of each. This template follows the rules of [is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/) and is used for a single post, regardless of post type. Themes that used the same code for both of those files (or included one in the other) can now simplify down to the one template.

## Archive.php

Unless a developer includes meta data with permalinks in their templates, the `archive.php` will not be used. Meta data is information tied to the post. For example the date something was posted on, the author, and any [categories, tags, or taxonomies](https://developer.wordpress.org/themes/functionality/categories-tags-custom-taxonomies/) used for the post are all examples of meta data. When a visitor to a website clicks on the meta data, the `archive.php` will render any posts associated with that piece of meta data. For example, if a visitor clicks on the name of an author, the `archive.php` will display all posts by that author.

Commonly, the title of the page being displayed by `archive.php` will be the name of the meta data the user clicked on. So if the user clicked on the Author’s name, the page name displaying all the other author’s posts will be the Author’s name and frequently there might be an additional description about the meta data. Here is a code example from Twenty Fifteen on their `archive.php` file. This snippet is the only piece of code that makes the `archive.php` file different from a `home.php` or `index.php` file.

```php
<header class="page-header">
    <?php
        the_archive_title( '<h1 class="page-title">', '</h1>' );
        the_archive_description( '<div class="taxonomy-description">', '</div>' );
    ?>
</header>
<!-- .page-header -->
```

## Author.php and Date.php

`Author.php` and `date.php` are more specific archive type files. If you need a refresher check out where they fit within the [template heirarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/). Generally, `archive.php` will suffice for most themes’ needs and you won’t need to create these templates.

### Author.php

If you are building a theme designed for multiple authors, it might make sense to build an author.php template. In the `author.php` template you could provide more information about an author, their gravatar, pull in their social media sites, and then all posts written by them. This would be a step up from relying just on the `archive.php` file.

Additionally, you can build specific `author.php` files for individual author’s by using their author ID or nicename. For example, say John Doe is the head author for a site with many guest authors. You may want all the guest authors’ information to display with author.php but you might build a specific author page with more information for John Doe by creating `author-johndoe.php` or `author-3.php` if his author ID is 3.

### Date.php

Similarly, if you are building a theme directed at magazine or news websites, a `date.php` file might make sense to build as these websites frequently organize their articles and posts by date or issue. Additionally, you could build a `day.php`, `month.php`, or `year.php` if you found enough justification for it.

## Category.php, Tag.php, and Taxonomy.php

If you need a refresher on what [categories, tags, & taxonomies](https://developer.wordpress.org/themes/basics/categories-tags-custom-taxonomies/) are you can look at their page. Often you won’t need to build out these template files. However, in an example of building a theme for food bloggers, there are some use cases for building these specific templates. In a food blogger website, the categories could be Great Restaurants, Beautiful Food, Ethnic Cuisine, and Recipes.

You might want most of your blog posts to display the same way except for any blogs that are categorized as recipes, because all recipes have ingredients and instrucitons sections. Therefore, you may want to build a `category-recipe.php` file to display your recipe blog posts in a grid view with some of the important details about the recipe visible.

Additionally, perhaps chocolate is a really important tag for the theme you’re building. It might make sense to build a `tag-chocolate.php` file so that you can display a specialized banner image of chocolate.

## Search.php

Most themes have a search.php file so it is clear to users that their query went through. It is common to have some sort of header identifying the query results such as this snippet found int twenty fifteen’s theme.

```php
<header class="page-header">
<h1 class="page-title">
    <?php printf( __( 'Search Results for: %s', 'twentyfifteen' ), get_search_query() ); ?>
</h1>
</header><!-- .page-header -->
```

This code snippet pulls in the query that was searched with `get_search_query()`. Often `search.php` will only pull in the excerpt instead of the full content since the user is trying to determine if the article or page fits their search.