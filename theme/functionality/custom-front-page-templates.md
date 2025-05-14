# Custom Front Page Templates

By default, WordPress shows your most recent posts in reverse chronological order on the front page of your site. Many WordPress users want a static front page or splash page as the front page instead. This “static front page” look is common for users desiring static or welcoming information on the front page of the site.

The look and feel of the front page of the site is based upon the choices of the user combined with the features and options of the WordPress Theme.

## Template Hierarchy of Custom Front Page

On the site front page, WordPress will always use the front-page.php template file, if it exists. If front-page.php does not exist, WordPress will determine which template file to use, depending on the user configuration of [Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") >Front page displays, as follows:

*   **A static page:** WordPress uses the [Static Page](https://codex.wordpress.org/Template_Hierarchy#Page_display "Template Hierarchy") template hierarchy:
    1.  [Custom Page Template](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates")
    2.  page-{id}.php
    3.  page-{slug}.php
    4.  page.php
    5.  index.php
*   **Your latest posts:** WordPress uses the [Blog Posts Index](https://codex.wordpress.org/Template_Hierarchy#Home_Page_display "Template Hierarchy") template hierarchy:
    1.  home.php
    2.  index.php

### Custom Site Front Page Template

To create a custom site front page template, include either of the following in the Theme:

*   front-page.php
*   A [Custom Page Template](https://codex.wordpress.org/Page_Templates#Custom_Page_Template "Page Templates") (e.g. template-featured.php for featured content)

### Custom Blog Posts Index Page Template

To create a custom blog posts index template, include the following in the Theme:

*   home.php

Use only the home.php template file for the blog posts index. Do not use a Custom Page Template (such as template-blog.php) for two reasons:

1.  When the static front page feature is configured properly, WordPress will not use a Custom Page Template to display the blog posts index, even if a Custom Page Template is assigned to the page designated as the “Posts page”. WordPress will *only* use either home.php or index.php.
2.  When the Custom Page Template is assigned to a static page other than the one designated as the “Posts page,” the blog posts index loop pagination will not work properly.

## Contextual Conditional Tags

### is\_front\_page

The [Conditional Tag](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [is\_front\_page()](https://codex.wordpress.org/Function_Reference/is_front_page) checks if the site front page is being displayed. Returns true when the site front page is being displayed, regardless of whether ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts” or “A static page”.

### is\_home

The [Conditional Tag](https://codex.wordpress.org/Conditional_Tags "Conditional Tags") [is\_home()](https://codex.wordpress.org/Function_Reference/is_home) checks if the blog posts index is being displayed. Returns true when the blog posts index is being displayed: when the site front page is being displayed and ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts”, or when ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “A static page” and the “Posts Page” value is the current [Page](https://codex.wordpress.org/Pages "Pages") being displayed.

When the site front page is being displayed and ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “Your latest posts”, both[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/) and [is\_home()](https://developer.wordpress.org/reference/functions/is_home/) will return true.

## Configuration of front-page.php

If it exists, the front-page.php template file is used on the site’s front page regardless of whether ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is set to “A static page” or “Your latest posts,” the Theme will need to account for both options, so that the site front page will display either a static page or the blog posts index. There are a few methods to do so.

### Conditional display within front-page.php

One way to allow front-page.php to account for both options for ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Front page displays’ is to add a conditional inside of front-page.php itself, using [get\_option( 'show\_on\_front' )](https://codex.wordpress.org/Option_Reference#Reading "Option Reference"), [get\_home\_template()](https://codex.wordpress.org/Function_Reference/get_home_template "Function Reference/get home template"), and[get\_page\_template()](https://codex.wordpress.org/Function_Reference/get_page_template "Function Reference/get page template").

Method 1: including custom content directly within front-page.php:  

```php
if ( 'posts' == get_option( 'show_on_front' ) ) {
    include( get_home_template() );
} else {
    // Custom content markup goes here
}
```

  
Method 2: including any page template:  

```php
if ( 'posts' == get_option( 'show_on_front' ) ) {
    include( get_home_template() );
} else {
    include( get_page_template() );
}
```

### Filtering frontpage\_template

Another way to allow the site front page to display either a static page/custom content or the blog posts index, without adding conditional code within front-page.php, is to [filter frontpage\_template](https://codex.wordpress.org/Function_Reference/get_query_template "Function Reference/get query template"), by adding a filter callback to functions.php:  

```php
function themeslug_filter_front_page_template( $template ) {
    return is_home() ? '' : $template;
}
add_filter( 'frontpage_template', 'themeslug_filter_front_page_template' );
```

  
This method causes WordPress to bypass the front-page.php template file altogether when the blog posts index is being displayed.

## Adding custom query loops to front-page.php

If the front-page.php template file includes a default [WordPress Loop](https://codex.wordpress.org/The_Loop "The Loop"), like so:  

```php
&lt;?php
if ( have_posts() ) : while ( have_posts() ) : the_post();
    // do something
endwhile; else:
    // no posts found
endif;
```

  
That loop applies to the post content of the static page assigned to ‘[Settings](https://codex.wordpress.org/Administration_Panels#Reading "Administration Panels") > [Reading](https://codex.wordpress.org/Settings_Reading_SubPanel "Settings Reading SubPanel") ->Posts page’.

To display custom loops (latest blog posts, custom/featured content, etc.), add secondary loop queries using calls to [WP\_Query](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query"). For example, to show the 3 latest blog posts:  

```php
$latest_blog_posts = new WP_Query( array( 'posts_per_page' =&gt; 3 ) );

if ( $latest_blog_posts-&gt;have_posts() ) : while ( $latest_blog_posts-&gt;have_posts() ) : $latest_blog_posts-&gt;the_post();
    // Loop output goes here
endwhile; endif;
```

## Pagination

Static front pages are not intended to be paged. None of the WordPress [Previous / Next page link](https://codex.wordpress.org/Next_and_Previous_Links "Next and Previous Links") functions work with a static front page. Pagination on a static front page uses the page query variable, not the paged variable. See the [WP\_Query](https://codex.wordpress.org/Class_Reference/WP_Query "Class Reference/WP Query") for details.