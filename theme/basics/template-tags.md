# Template Tags

Template tags are used within themes to **retrieve content from your database**. The content could be anything from a blog title to a complete sidebar. Template tags are the preferred method to pull content into your theme because:

*   they can print dynamic content;
*   they can be used in multiple theme files; and
*   they separate the theme into smaller, more understandable, sections.

## What is a Template Tag?

A template tag is simply a piece of code that tells WordPress to get something from the database. It is broken up into three components:

*   A PHP code tag
*   A WordPress function
*   Optional parameters

You can use a template tag to call another theme file or some information from the database.

For example, the template tag `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` tells WordPress to get the `header.php` file and include it in the current theme file. Similarly, `[get_footer()](https://developer.wordpress.org/reference/functions/get_footer/)` tells WordPress to get the footer.php file.

There are also other kinds of template tags:

*   `[the_title()](https://developer.wordpress.org/reference/functions/the_title/)` – tells WordPress to get the title of the page or post from the database and include it.
*   `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` – tells WordPress to get the blog title out of the database and include it in the template file.

If you look closely at the last example, you will also see that there is a parameter between the parenthesis. Parameters let you do two things:

1.  ask for specific pieces of information and
2.  format the information in a certain way.

[Parameters are covered extensively below](#parameters), but it’s useful to be aware that you can send WordPress-specific instructions for how you want the data presented.

## Why Use Template Tags

By encapsulating all of the code for a particular chunk of content, template tags make it very easy to include various pieces of a template in a theme file and also to maintain the theme.

It is far easier to create one `header.php` file and have all of your theme templates like `single.php`, `page.php`, `front-page.php`, etc. reference that one theme file using `[get_header()](https://developer.wordpress.org/reference/functions/get_header/)` than copying and pasting the code into each theme file. It also makes maintenance easier. Whenever you make a change in your `header.php` file, the change is automatically carried over into all of your other theme files.

Another reason to use template tags is to display dynamic data, i.e. data from the database. In your header, you could manually include the `title` tag, like so:

```xml
<title>My Personal Website</title>
```

However, doing this means manually editing your theme any time you want to change the title of your website. Instead, it’s easier to include the `[bloginfo( 'name' )](https://developer.wordpress.org/reference/functions/bloginfo/)` template tag, which automatically fetch the site title from the database. Now, you can change the title of your site in WordPress, rather than having to hard code your theme templates.

## How to Use Template Tags

Using template tags is very simple. In any template file you can use a template tag by simply printing one line of php code to call the template tag. Printing the header.php file is as simple as:

```php
get_header();
```

### Parameters

Some template tags let you pass parameters. Parameters are extra pieces of information that determine what is retrieved from the database.

For example, the `[bloginfo()](https://developer.wordpress.org/reference/functions/bloginfo/ "bloginfo template tag")` template tag allows you to give it a parameter telling WordPress the specific piece of information you want. To print the blog name, you just pass along the parameter “name,” like so:

```php
bloginfo( 'name' );
```

To print the version of WordPress that the blog is running on, you would pass a parameter of “version”:

```php
bloginfo( 'version' );
```

For each template tag, the parameters differ. A list of the parameters and what they can do can be found on specific template tag pages located throughout the [code reference](https://developer.wordpress.org/reference/).

### Using Template Tags Within the Loop

Many template tags work within the [WordPress Loop](https://developer.wordpress.org/themes/basics/the-loop/). This means that they are included in the template files as part of the php “loop” that generates the pages users see based upon the instructions inside of the loop.

The WordPress loop begins with:

```php
if ( have_posts() ) :
	while ( have_posts() ) :
		the_post();
```

Template tags that work within the loop must be in the middle area, before the ending section of the loop below:

```php
	endwhile;
else :
	_e( 'Sorry, no posts matched your criteria.', 'devhub' );
endif;
```

Some of template tags that need to be inside of the loop include

*   [the\_content()](https://developer.wordpress.org/reference/functions/the_content/)
*   [the\_excerpt()](https://developer.wordpress.org/reference/functions/the_excerpt/)
*   [next\_post()](https://developer.wordpress.org/reference/functions/next_post/)
*   [previous\_post()](https://developer.wordpress.org/reference/functions/previous_post/)

The main reason why some functions require the loop is because they require the global post object to be set.

If the template tag you want to use doesn’t have to be within the loop

*   [wp\_list\_cats()](https://developer.wordpress.org/reference/functions/wp_list_cats/)
*   [wp\_list\_pages()](https://developer.wordpress.org/reference/functions/wp_list_pages/)

then you can put it in any file you’d like, for instance in the sidebar, header, or footer template files.

These are functions that typically do not require the global post object.

## See Also

*   [Conditional Tags](https://developer.wordpress.org/themes/basics/conditional-tags/)
*   [Complete list of Template Tags](https://developer.wordpress.org/themes/references/list-of-template-tags/)
*   [Plugin API Hooks](_wp_link_placeholder)