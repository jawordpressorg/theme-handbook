# Conditional Tags

Conditional Tags can be used in your Template Files in classic themes to alter the display of content depending on the conditions that the current page matches. They tell WordPress what code to display under specific conditions. Conditional Tags usually work with PHP [if](http://php.net/manual/en/control-structures.if.php "PHP if conditional") /[else](http://php.net/manual/en/control-structures.else.php "PHP else conditional") Conditional Statements.

The code begins by checking to see **if** a statement is true or false. If the statement is found to be true, the first set of code is executed. If it’s false, the first set of code is skipped, and the second set of code (after the **else**) is executed instead.

For example, you could ask if a user is logged in, and then provide a different greeting depending on the result.

    if ( is\_user\_logged\_in() ):
        echo 'Welcome, registered user!';
    else:
        echo 'Welcome, visitor!';
    endif;

Note the close relation these tags have to [WordPress Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/).

## Where to Use Conditional Tags

For a Conditional Tag to modify your data, the information must already have been retrieved from your database, i.e. the query must have already run. If you use a Conditional Tag before there is data, there’ll be nothing to ask the if/else statement about.

It’s important to note that WordPress loads `functions.php` before the query is run, so if you simply include a Conditional Tag in that file, it won’t work.

Two ways to implement Conditional Tags:

*   place it in a [Template File](https://developer.wordpress.org/themes/basics/template-files/)
*   create a function out of it in `functions.php` that hooks into an action/filter that triggers at a later point

## The Conditions For

Listed below are the conditions under which each of the following **conditional statements proves to be true**. Tags which can accept parameters are noted.

### The Main Page

[](https://developer.wordpress.org/reference/functions/is_home/ "Function_Reference/is_home")[is\_home()](https://developer.wordpress.org/reference/functions/is_home/)

This condition returns true when the main blog page is being displayed, usually in standard reverse chronological order. If your home page has been set to a Static Page instead, then this will only prove true on the page which you set as the “Posts page” in Settings > Reading.

### The Front Page

[](https://developer.wordpress.org/reference/functions/is_front_page/ "Function_Reference/is_front_page")[is\_front\_page()](https://developer.wordpress.org/reference/functions/is_front_page/)

This condition returns true when the front page of the site is displayed, regardless of whether it is set to show posts or a static page.

Returns true when:

1.  the main blog page is being displayed **and**
2.  the Settings > Reading -> *Front page displays* option is set to *Your latest posts*

**OR**

1.  when Settings > Reading -> *Front page displays* is set to *A static page* **and**
2.  the Front Page value is the current Page being displayed.

### The Administration Panels

[](https://developer.wordpress.org/reference/functions/is_admin/ "Function_Reference/is_admin")[is\_admin()](https://developer.wordpress.org/reference/functions/is_admin/)

This condition returns true when the Dashboard or the administration panels are being displayed.

### A Single Post Page

[](https://developer.wordpress.org/reference/functions/is_single/ "Function_Reference/is_single")[is\_single()](https://developer.wordpress.org/reference/functions/is_single/)

Returns true when any single Post (or attachment, or custom Post Type) is being displayed. This condition returns false if you are on a page.

**is\_single( ’17’ )**

[is\_single()](https://developer.wordpress.org/reference/functions/is_single/) can also check for certain posts by ID and other parameters. The above example proves true when Post 17 is being displayed as a single Post.

**is\_single( ‘Irish Stew’ )**

Parameters include Post titles, as well. In this case, it proves true when the Post with title “Irish Stew” is being displayed as a single Post.

**is\_single( ‘beef-stew’ )**

Proves true when the Post with Post Slug “beef-stew” is being displayed as a single Post.

**is\_single( array( 17, ‘beef-stew’, ‘Irish Stew’ ) )**

Returns true when the single post being displayed is either post ID 17, or the post\_name is “beef-stew”, or the post\_title is “Irish Stew”.

**is\_single( array( 17, 19, 1, 11 ) )**

Returns true when the single post being displayed is either post ID = 17, post ID = 19, post ID = 1 or post ID = 11.

**is\_single( array( ‘beef-stew’, ‘pea-soup’, ‘chilli’ ) )**

Returns true when the single post being displayed is either the post\_name “beef-stew”, post\_name “pea-soup” or post\_name “chilli”.

**is\_single( array( ‘Beef Stew’, ‘Pea Soup’, ‘Chilli’ ) )**

Returns true when the single post being displayed is either the post\_title is “Beef Stew”, post\_title is “Pea Soup” or post\_title is “Chilli”.

Note: This function does not distinguish between the post ID, post title, or post name. A post named “17” would be displayed if a post ID of 17 was requested. Presumably the same holds for a post with the slug “17”.

### A Single Post, Page, or Attachment

[](https://developer.wordpress.org/reference/functions/is_singular/)[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)

Returns true for any is\_single, is\_page, and is\_attachment. It does allow testing for post types.

### A Sticky Post

[](https://developer.wordpress.org/reference/functions/is_sticky/ "Function_Reference/is_sticky")[is\_sticky()](https://developer.wordpress.org/reference/functions/is_sticky/)

Returns true if the “Stick this post to the front page” check box has been checked for the current post. In this example, no post ID argument is given, so the post ID for the Loop post is used.

**is\_sticky( ’17’ )**  
Returns true when Post 17 is considered a sticky post.

### A Post Type

[](https://developer.wordpress.org/reference/functions/get_post_type/ "Function_Reference/get_post_type")[get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/)

You can test to see if the current post is of a certain type by including [](https://developer.wordpress.org/reference/functions/get_post_type/ "Function Reference/get_post_type")[get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/) in your conditional. It’s not really a conditional tag, but it returns the [registered post type](https://developer.wordpress.org/reference/functions/register_post_type/ "Function Reference/Register Post Type") of the current post.

**if ( ‘book’ == [get\_post\_type()](https://developer.wordpress.org/reference/functions/get_post_type/) ) …**

[](https://developer.wordpress.org/reference/functions/post_type_exists/ "Function Reference/post_type_exists")[post\_type\_exists()](https://developer.wordpress.org/reference/functions/post_type_exists/)

Returns true if a given post type is a registered post type. This does not test if a post is a certain post\_type. Note: This function replaces a function called is\_post\_type which existed briefly in 3.0 development.

### A Post Type is Hierarchical

[is\_post\_type\_hierarchical( $post\_type )](https://developer.wordpress.org/reference/functions/is_post_type_hierarchical/ "Function-reference/is_post_type_hierarchical/")

Returns true if this $post\_type has been set with hierarchical support when registered.

**is\_post\_type\_hierarchical( ‘book’ )**

Returns true if the book post type was registered as having support for hierarchical.

###  A Post Type Archive

[](https://developer.wordpress.org/reference/functions/is_post_type_archive/ "Function_Reference/is_post_type_archive")[is\_post\_type\_archive()](https://developer.wordpress.org/reference/functions/is_post_type_archive/)

Returns true on any post type archive.

**is\_post\_type\_archive( $post\_type )**

Returns true if on a post type archive page that matches $post\_type (can be a single post type or an array of post types).

To turn on post type archives, use ‘has\_archive’ => true, when [registering the post type](https://make.wordpress.org/docs/plugin-developer-handbook/9-custom-post-types-and-taxonomies/registering-custom-post-types/ "Function_Reference/register_post_type").

### Any Page Containing Posts

[](https://developer.wordpress.org/reference/functions/comments_open/ "Function_Reference/comments_open")[comments\_open()](https://developer.wordpress.org/reference/functions/comments_open/)

When comments are allowed for the current Post being processed in the [WordPress Loop](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/the-loop/ "The Loop").

[](https://developer.wordpress.org/reference/functions/pings_open/ "Function_Reference/pings_open")[pings\_open()](https://developer.wordpress.org/reference/functions/pings_open/)

When pings are allowed for the current Post being processed in the WordPress Loop.

### A “PAGE” Page

This section refers to WordPress Pages, not any generic webpage from your blog, or in other words to the built in *post\_type* ‘page’.

[](https://developer.wordpress.org/reference/functions/is_page/ "Function_Reference/is_page")[is\_page()](https://developer.wordpress.org/reference/functions/is_page/)

When any Page is being displayed.

**is\_page( ’42’ )**

When Page 42 (ID) is being displayed.

**is\_page( ‘About Me And Joe’ )**

When the Page with a *post\_title* of “About Me And Joe” is being displayed.

**is\_page( ‘about-me’ )**

When the Page with a *post\_name* (slug) of “about-me” is being displayed.

**is\_page( array( 42, ‘about-me’, ‘About Me And Joe’ ) )**

Returns true when the Pages displayed is either *post ID* = 42, or *post\_name* is “about-me”, or *post\_title* is “About Me And Joe”.

**is\_page( array( 42, 54, 6 ) )**

Returns true when the Pages displayed is either *post ID* = 42, or *post ID* = 54, or *post ID* = 6.

#### Testing for Paginated Pages

You can use this code to check whether you’re on the nth page in a Post or Page that has been divided into pages using the `<!--nextpage-->` QuickTag. This can be useful, for example, if you wish to display meta-data only on the first page of a post divided into several pages.

##### Example 1

<?php
  $paged = $wp\_query->get( 'page' );
  if ( ! $paged || $paged < 2 ) {
    // This is not a paginated page (or it's simply the first page of a paginated page/post)    } else {
    // This is a paginated page.
} ?>

##### Example 2

<?php $paged = get\_query\_var( 'page' ) ? get\_query\_var( 'page' ) : false;
    if ( $paged == false )  {
    // This is not a paginated page (or it's simply the first page of a paginated page/post) }  else  {
    // This is a paginated page.
    }
?>

#### Testing for Sub-Pages

There is no `is_subpage()` function, but you can test this with a little code:

**Snippet 1**

<?php  global $post; // if outside the loop
   if ( is\_page() && $post->post\_parent ) {
     // This is a subpage
   } else {
     // This is not a subpage
   }
?>

You can create your own is\_subpage() function using the code in Snippet 2. Add it to your functions.php file. It tests for a parent page in the same way as Snippet 1, but will return the ID of the page parent if there is one, or false if there isn’t.

**Snippet 2**

function is\_subpage() {
    global $post;                              // load details about this page

    if ( is\_page() && $post->post\_parent ) {   // test to see if the page has a parent
        return $post->post\_parent;             // return the ID of the parent post

    } else {                                   // there is no parent so ...
        return false;                          // ... the answer to the question is false
    }
}

It is advisable to use a function like that in Snippet 2, rather than using the simple test like Snippet 1, if you plan to test for sub-pages frequently.

To test if the parent of a page is a specific page, for instance “About” (page id pid 2 by default), we can use the tests in Snippet 3. These tests check to see if we are looking at the page in question, as well as if we are looking at any child pages. This is useful for setting variables specific to different sections of a web site, so a different banner image, or a different heading.

**Snippet 3**

<?php if ( is\_page( 'about' ) || '2' == $post->post\_parent ) {
    // the page is "About", or the parent of the page is "About"
    $bannerimg = 'about.jpg';
} elseif ( is\_page( 'learning' ) || '56' == $post->post\_parent ) {
    $bannerimg = 'teaching.jpg';
} elseif ( is\_page( 'admissions' ) || '15' == $post->post\_parent ) {
    $bannerimg = 'admissions.jpg';
} else {
    $bannerimg = 'home.jpg'; // just in case we are at an unclassified page, perhaps the home page
}
?>

Snippet 4 is a function that allows you to carry out the tests above more easily. This function will return true if we are looking at the page in question (so “About”) or one of its sub pages (so a page with a parent with ID “2”).

**Snippet 4**

function is\_tree( $pid ) {      // $pid = The ID of the page we're looking for pages underneath
    global $post;               // load details about this page

    if ( is\_page($pid) )
        return true;            // we're at the page or at a sub page

    $anc = get\_post\_ancestors( $post->ID );
    foreach ( $anc as $ancestor ) {
        if( is\_page() && $ancestor == $pid ) {
            return true;
        }
    }

    return false;  // we aren't at the page, and the page is not an ancestor
}

Add Snippet 4 to your functions.php file, and call is\_tree( ‘id’ ) to see if the current page is the page, or is a sub page of the page. In Snippet 3, is\_tree( ‘2’ ) would replace “is\_page( ‘about’ ) || ‘2’ == $post->post\_parent” inside the first if tag.

Note that if you have more than one level of pages the parent page is the one directly above and not the one at the very top of the hierarchy.

### Is a Page Template

Allows you to determine whether or not you are in a page template or if a specific page template is being used.

[](https://developer.wordpress.org/reference/functions/is_page_template/ "Function reference/page template")[is\_page\_template()](https://developer.wordpress.org/reference/functions/is_page_template/)

Is a Page Template being used?

**is\_page\_template( ‘about.php’ )**

Is Page Template ‘about’ being used? Note that unlike other conditionals, if you want to specify a particular Page Template, you need to use the filename, such as about.php or my\_page\_template.php.

Note: if the file is in a subdirectory you must include this as well. Meaning that this should be the filepath in relation to your theme as well as the filename, for example ‘page-templates/about.php’.

### A Category Page

[](https://developer.wordpress.org/reference/functions/is_category/ "Function reference/is category")[is\_category()](https://developer.wordpress.org/reference/functions/is_category/)

When a Category archive page is being displayed.

**is\_category( ‘9’ )**

When the archive page for Category 9 is being displayed.

**is\_category( ‘Stinky Cheeses’ )**

When the archive page for the Category with Name “Stinky Cheeses” is being displayed.

**is\_category( ‘blue-cheese’ )**

When the archive page for the Category with Category Slug “blue-cheese” is being displayed.

**is\_category( array( 9, ‘blue-cheese’, ‘Stinky Cheeses’ ) )**

Returns true when the category of posts being displayed is either term\_ID 9, or slug “blue-cheese”, or name “Stinky Cheeses”.

**in\_category( ‘5’ )**

Returns true if the current post is in the specified category id.

**in\_category( array( 1, 2, 3 ) )**

Returns true if the current post is in either category 1, 2, or 3.

**! in\_category( array( 4, 5, 6 ) )**

Returns true if the current post is NOT in either category 4, 5, or 6. Note the ! at the beginning.

Note: Be sure to check your spelling when testing. There’s a big difference between “is” or “in”.

See also [](https://developer.wordpress.org/reference/functions/is_archive/ "Function reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/) and [Category Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#category "Template Hierarchy / Category templates").

### A Tag Page

[](https://developer.wordpress.org/reference/functions/is_tag/ "Function reference/is tag")[is\_tag()](https://developer.wordpress.org/reference/functions/is_tag/)

When any Tag archive page is being displayed.

**is\_tag( ‘mild’ )**

When the archive page for tag with the slug of ‘mild’ is being displayed.

**is\_tag( array( ‘sharp’, ‘mild’, ‘extreme’ ) )**

Returns true when the tag archive being displayed has a slug of either “sharp”, “mild”, or “extreme”.

**[has\_tag()](https://developer.wordpress.org/reference/functions/has_tag/)**

When the current post has a tag. Must be used inside The Loop.

**has\_tag( ‘mild’ )**

When the current post has the tag ‘mild’.

**has\_tag( array( ‘sharp’, ‘mild’, ‘extreme’ ) )**

When the current post has any of the tags in the array.

See also [](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/) and [Tag Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#tag "Template hierarchy/Tag template").

### A Taxonomy Page

[](https://developer.wordpress.org/reference/functions/is_tax/ "Function Reference/is tax")[is\_tax()](https://developer.wordpress.org/reference/functions/is_tax/)

When any Taxonomy archive page is being displayed.

**is\_tax( ‘flavor’ )**

When a Taxonomy archive page for the flavor taxonomy is being displayed.

**is\_tax( ‘flavor’, ‘mild’)**

When the archive page for the flavor taxonomy with the slug of ‘mild’ is being displayed.

**is\_tax( ‘flavor’, array( ‘sharp’, ‘mild’, ‘extreme’ ) )**

Returns true when the flavor taxonomy archive being displayed has a slug of either “sharp”, “mild”, or “extreme”.

[](https://developer.wordpress.org/reference/functions/has_term/)[has\_term()](https://developer.wordpress.org/reference/functions/has_term/)

Check if the current post has any of given terms. The first parameter should be an empty string. It expects a taxonomy slug/name as a second parameter.

**has\_term( ‘green’, ‘color’ )**

When the current post has the term ‘green’ from taxonomy ‘color’.

**has\_term( array( ‘green’, ‘orange’, ‘blue’ ), ‘color’ )**

When the current post has any of the terms in the array.

See also [](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/) .

### A Registered Taxonomy

[](https://developer.wordpress.org/reference/functions/taxonomy_exists/ "Function Reference/taxonomy exists")[taxonomy\_exists()](https://developer.wordpress.org/reference/functions/taxonomy_exists/)

When a particular taxonomy is registered via [](https://developer.wordpress.org/reference/functions/register_taxonomy/ "Function Reference/Register Taxonomy")[register\_taxonomy()](https://developer.wordpress.org/reference/functions/register_taxonomy/) . Formerly [is\_taxonomy()](https://developer.wordpress.org/reference/functions/is_taxonomy/) , which was deprecated in Version 3.0

### An Author Page

[](https://developer.wordpress.org/reference/functions/is_author/ "Function Reference/is author")[is\_author()](https://developer.wordpress.org/reference/functions/is_author/)

When any Author page is being displayed.

**is\_author( ‘4’ )**

When the archive page for Author number (ID) 4 is being displayed.

**is\_author( ‘Vivian’ )**

When the archive page for the Author with Nickname “Vivian” is being displayed.

**is\_author( ‘john-jones’ )**

When the archive page for the Author with Nicename “john-jones” is being displayed.

**is\_author( array( 4, ‘john-jones’, ‘Vivian’ ) )**

When the archive page for the author is either user ID 4, or user\_nicename “john-jones”, or nickname “Vivian”.

See also [](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/) and [Author Templates](https://make.wordpress.org/docs/theme-developer-handbook/part-one-theme-basics/template-hierarchy/#author-display).

### A Multi-author Site

[](https://developer.wordpress.org/reference/functions/is_multi_author/ "Function Reference/is multi author")[is\_multi\_author()](https://developer.wordpress.org/reference/functions/is_multi_author/)

When more than one author has published posts for a site. Available with Version 3.2.

### A Date Page

[](https://developer.wordpress.org/reference/functions/is_date/ "Function Reference/is date")[is\_date()](https://developer.wordpress.org/reference/functions/is_date/)

When any date-based archive page is being displayed (i.e. a monthly, yearly, daily or time-based archive).

[](https://developer.wordpress.org/reference/functions/is_year/ "Function Reference/is year")[is\_year()](https://developer.wordpress.org/reference/functions/is_year/)

When a yearly archive is being displayed.

[](https://developer.wordpress.org/reference/functions/is_month/ "Function Reference/is month")[is\_month()](https://developer.wordpress.org/reference/functions/is_month/)

When a monthly archive is being displayed.

[](https://developer.wordpress.org/reference/functions/is_day/ "Function Reference/is day")[is\_day()](https://developer.wordpress.org/reference/functions/is_day/)

When a daily archive is being displayed.

[](https://developer.wordpress.org/reference/functions/is_time/ "Function Reference/is time")[is\_time()](https://developer.wordpress.org/reference/functions/is_time/)

When an hourly, “minutely”, or “secondly” archive is being displayed.

[](https://developer.wordpress.org/reference/functions/is_new_day/ "Function Reference/is new day")[is\_new\_day()](https://developer.wordpress.org/reference/functions/is_new_day/)

If today is a new day according to post date. Should be used inside the loop.

### Any Archive Page

[](https://developer.wordpress.org/reference/functions/is_archive/ "Function Reference/is archive")[is\_archive()](https://developer.wordpress.org/reference/functions/is_archive/)

When any type of Archive page is being displayed. Category, Tag, Author and Date based pages are all types of Archives.

### A Search Result Page

[](https://developer.wordpress.org/reference/functions/is_search/ "Function Reference/is search")[is\_search()](https://developer.wordpress.org/reference/functions/is_search/)

When a search result page archive is being displayed.

### A 404 Not Found Page

[](https://developer.wordpress.org/reference/functions/is_404/ "Function Reference/is 404")[is\_404()](https://developer.wordpress.org/reference/functions/is_404/)

When a page displays after an “HTTP 404: Not Found” error occurs.

### A Privacy Policy Page

[](https://developer.wordpress.org/reference/functions/is_privacy_policy/)[is\_privacy\_policy()](https://developer.wordpress.org/reference/functions/is_privacy_policy/)

When the Privacy Policy page is being displayed.

### An Attachment

[](https://developer.wordpress.org/reference/functions/is_attachment/ "Function Reference/is attachment")[is\_attachment()](https://developer.wordpress.org/reference/functions/is_attachment/)

When an attachment document to a post or Page is being displayed. An attachment is an image or other file uploaded through the post editor’s upload utility. Attachments can be displayed on their own ‘page’ or template.

### A Single Page, Single Post or Attachment

[](https://developer.wordpress.org/reference/functions/is_singular/ "Function Reference/is singular")[is\_singular()](https://developer.wordpress.org/reference/functions/is_singular/)

When any of the following return true: `is_single()`, `is_page()` or `is_attachment()`.

**is\_singular( ‘book’ )**

True when viewing a post of the Custom Post Types book.

**is\_singular( array( ‘newspaper’, ‘book’ ) )**

True when viewing a post of the Custom Post Types newspaper or book.

### A Syndication

[](https://developer.wordpress.org/reference/functions/is_feed/ "Function Reference/is feed")[is\_feed()](https://developer.wordpress.org/reference/functions/is_feed/)

When the site requested is a Syndication. This tag is not typically used by users; it is used internally by WordPress and is available for Plugin Developers.

### A Trackback

[](https://developer.wordpress.org/reference/functions/is_trackback/ "Function Reference/is trackback")[is\_trackback()](https://developer.wordpress.org/reference/functions/is_trackback/)

When the site requested is WordPress’ hook into its Trackback engine. This tag is not typically used by users; it is used internally by WordPress and is available for Plugin Developers.

### A Preview

[](https://developer.wordpress.org/reference/functions/is_preview/ "Function Reference/is preview")[is\_preview()](https://developer.wordpress.org/reference/functions/is_preview/)

When a single post being displayed is viewed in Draft mode.

### Has An Excerpt

[](https://developer.wordpress.org/reference/functions/has_excerpt/ "Function Reference/has excerpt")[has\_excerpt()](https://developer.wordpress.org/reference/functions/has_excerpt/)

When the current post has an excerpt

**has\_excerpt( 42 )**

When the post 42 (ID) has an excerpt.

<?php // Get $post if you're inside a function global $post;
   if ( empty( $post->post\_excerpt ) ) {
    // This post has no excerpt
   } else {
    // This post has excerpt
  }
?>

**Other use**  
When you need to hide the auto displayed excerpt and only display your post’s excerpts.

<?php
  if ( ! has\_excerpt() ) {
      echo '';
  } else {
      the\_excerpt();
  }
?>

Replace auto excerpt for a text or code.

<?php if ( ! has\_excerpt() ) {
    // your text or code
} ?>

### Has A Nav Menu Assigned

[](https://developer.wordpress.org/reference/functions/has_nav_menu/ "Function Reference/has nav menu")[has\_nav\_menu()](https://developer.wordpress.org/reference/functions/has_nav_menu/)

Whether a registered nav menu location has a menu assigned

Returns: assigned(true) or not(false)

### Inside The Loop

[](https://developer.wordpress.org/reference/functions/in_the_loop/ "Function Refence/in the loop")[in\_the\_loop()](https://developer.wordpress.org/reference/functions/in_the_loop/)

Check to see if you are “inside the loop”. Useful for plugin authors, this conditional returns as true when you are inside the loop.

### Is Sidebar Active

[](https://developer.wordpress.org/reference/functions/is_active_sidebar/ "Function Reference/is active sidebar")[is\_active\_sidebar()](https://developer.wordpress.org/reference/functions/is_active_sidebar/)

Check to see if a given sidebar is active (in use). Returns true if the sidebar (identified by name, id, or number) is in use, otherwise the function returns false.

### Part of a Network (Multisite)

[](https://developer.wordpress.org/reference/functions/is_multisite/ "Function Reference/is multisite")[is\_multisite()](https://developer.wordpress.org/reference/functions/is_multisite/)

Check to see whether the current site is in a WordPress MultiSite install.

### Main Site (Multisite)

[](https://developer.wordpress.org/reference/functions/is_main_site/ "Function Reference/is main site")[is\_main\_site()](https://developer.wordpress.org/reference/functions/is_main_site/)

Determines if a site is the main site in a network.

### Admin of a Network (Multisite)

[](https://developer.wordpress.org/reference/functions/is_super_admin/ "Function Reference/is super admin")[is\_super\_admin()](https://developer.wordpress.org/reference/functions/is_super_admin/)

Determines if a user is a network (super) admin.

### An Active Plugin

[](https://developer.wordpress.org/reference/functions/is_plugin_active/ "Function Reference/is plugin active")[is\_plugin\_active()](https://developer.wordpress.org/reference/functions/is_plugin_active/)

Checks if a plugin is activated.

### A Child Theme

[](https://developer.wordpress.org/reference/functions/is_child_theme/ "Function Reference/is child theme")[is\_child\_theme()](https://developer.wordpress.org/reference/functions/is_child_theme/)

Checks whether a child theme is in use.

### Theme supports a feature

[](https://developer.wordpress.org/reference/functions/current_theme_supports/ "Function Reference/current theme supports")[current\_theme\_supports()](https://developer.wordpress.org/reference/functions/current_theme_supports/)

Checks if various theme features exist.

## Working Examples

Here are working samples to demonstrate how to use these conditional tags.

### Single Post

This example shows how to use `[is_single()](https://developer.wordpress.org/reference/functions/is_single/)` to display something specific only when viewing a single post page:

if ( is\_single() ) {

   echo 'This is just one of many fabulous entries in the ' . single\_cat\_title() . ' category!';

}

Another example of how to use Conditional Tags in the Loop. Choose to display content or excerpt in index.php when this is a display single post or the home page.

if ( is\_home() || is\_single() ) {

   the\_content();

}
else {

   the\_excerpt();

}

When you need display a code or element, in a place that is NOT the home page.

<?php if ( ! is\_home() ) {

 // Insert your markup ...

} ?>

### Check for Multiple Conditionals

You can use [PHP operators](https://www.php.net/manual/en/language.operators.php) to evaluate multiple conditionals in a single if statement.

This is handy if you need to check whether combinations of conditionals evaluate to true or false.

// Check to see if any of 2 conditionals are met
if ( is\_single() || is\_page() ) {
 // If it's a single post or a single page, do something special
}

if ( is\_archive() && ! is\_category( 'nachos' ) ) {
 // If it's an archive page for any category EXCEPT nachos, do something special
}

// Check to see if 3 conditionals are met
if ( $query->is\_main\_query() && is\_post\_type\_archive( 'products' ) && ! is\_admin() ) {

 // If it's the main query on a custom post type archive for Products
 // And if we're not in the WordPress admin, then do something special

}
if ( is\_post\_type\_archive( 'movies' ) || is\_tax( 'genre' ) || is\_tax( 'actor' )  ) {
 // If it's a custom post type archive for Movies
 // Or it's a taxonomy archive for Genre
 // Or it's a taxonomy archive for Actor, do something special
}

### Date Based Differences

If someone browses our site by date, let’s distinguish posts in different years by using different colors:

<?php // this starts The Loop
if ( have\_posts() ) : while ( have\_posts() ) : the\_post(); ?>
<h2 id="post-<?php the\_ID(); ?>">
<a href="<?php the\_permalink() ?>" rel="bookmark"><?php the\_title(); ?></a></h2>

<small><?php the\_time('F jS, Y') ?> by <?php the\_author() ?></small>

<?php
// are we showing a date-based archive?
if ( is\_date() ) {
 if ( date( 'Y' ) != get\_the\_date( 'Y' ) ) {
 // this post was written in a previous year
 // so let's style the content using the "oldentry" class
 echo '<div class="oldentry">';
 } else {
 echo '<div class="entry">';
 }
} else {
 echo '<div class="entry">';
}

the\_content( 'Read the rest of this entry »' );
?></div>

### Variable Sidebar Content

This example will display different content in your sidebar based on what page the reader is currently viewing.

<div id="sidebar">
<?php // let's generate info appropriate to the page being displayed
if ( is\_home() ) {
 // we're on the home page, so let's show a list of all top-level categories
    wp\_list\_categories( 'optionall=0&sort\_column=name&list=1&children=0' );
} elseif ( is\_category() ) {
 // we're looking at a single category view, so let's show \_all\_ the categories
    wp\_list\_categories( 'optionall=1&sort\_column=name&list=1&children=1&hierarchical=1' )
} elseif ( is\_single() ) {
 // we're looking at a single page, so let's not show anything in the sidebar
} elseif ( is\_page() ) {
 // we're looking at a static page. Which one?
 if ( is\_page( 'About' ) ) {
 // our about page.
 echo "This is my about page!";
 } elseif ( is\_page( 'Colophon' ) ) {
 echo "This is my colophon page, running on WordPress " . bloginfo( 'version' ) . "";
 } else {
 // catch-all for other pages
 echo "Vote for Pedro!";
 }
} else {
 // catch-all for everything else (archives, searches, 404s, etc)
 echo "Pedro offers you his protection.";
} // That's all, folks!
?>
</div>

### Helpful 404 Page

The [Creating an Error 404 Page](https://codex.wordpress.org/Creating_an_Error_404_Page) articleh as an example of using the PHP conditional function `isset()` in the [Writing Friendly Messages](https://codex.wordpress.org/Creating_an_Error_404_Page#Writing_Friendly_Messages) section.

### In the theme’s footer.php file

At times queries performed in other templates such as sidebar.php may corrupt certain conditional tags. For instance, in header.php a conditional tag works properly but doesn’t work in a theme’s footer.php. The trick is to put wp\_reset\_query before the conditional test in the footer. For example:

<?php wp\_reset\_query();
 if ( is\_page( '2' ) ) {
  echo 'This is page 2!';
 }
?>

## Conditional Tags Index

> [List of Conditional Tags](https://developer.wordpress.org/themes/references/list-of-conditional-tags/)

## Function Reference

[Reference](https://developer.wordpress.org/?s=is_)