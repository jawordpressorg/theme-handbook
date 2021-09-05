# Sticky Posts

A Sticky Post is the post will be placed at the top of the front page of posts. This feature is only available for the built-in post type post and not for custom post types.

## How to stick a post

1.  Go to **Administration Screen > Posts > Add New** or **Edit**
2.  In the right side menu, Click Edit link of Visibility option in Publish group
3.  Click Stick this post to the front page option

![](https://developer.wordpress.org/files/2017/01/sticked_post.jpg)

## Display Sticky Posts

### Show Sticky Posts

Display just the first sticky post. At least one post must be designated as a “sticky post” or else the loop will display all posts:

</p>
$sticky = get\_option( 'sticky\_posts' );
$query = new WP\_Query( 'p=' . $sticky\[0\] );
<p>

Display just the first sticky post, if none return the last post published:

</p>
$args = array(
        'posts\_per\_page' => 1,
        'post\_\_in' => get\_option( 'sticky\_posts' ),
        'ignore\_sticky\_posts' => 1
);
$query = new WP\_Query( $args );
<p>

Display just the first sticky post, if none return nothing:

</p>
$sticky = get\_option( 'sticky\_posts' );
$args = array(
        'posts\_per\_page' => 1,
        'post\_\_in' => $sticky,
        'ignore\_sticky\_posts' => 1
);
$query = new WP\_Query( $args );
if ( isset( $sticky\[0\] ) ) {
    // insert here your stuff...
}
<p>

### Don’t Show Sticky Posts

Exclude all sticky posts from the query:

</p>
$query = new WP\_Query( array( 'post\_\_not\_in' => get\_option( 'sticky\_posts' ) ) );
<p>

Exclude sticky posts from a category. Return ALL posts within the category, but don’t show sticky posts at the top. The ‘sticky posts’ will still show in their natural position (e.g. by date):

</p>
$query = new WP\_Query( 'ignore\_sticky\_posts=1&posts\_per\_page=3&cat=6' );
<p>

Exclude sticky posts from a category. Return posts within the category, but exclude sticky posts completely, and adhere to paging rules:

</p>
$paged = get\_query\_var( 'paged' ) ? get\_query\_var( 'paged' ) : 1;
$sticky = get\_option( 'sticky\_posts' );
$args = array(
        'cat' => 3,
        'ignore\_sticky\_posts' => 1,
        'post\_\_not\_in' => $sticky,
        'paged' => $paged
);
$query = new WP\_Query( $args );
<p>

Note: Use get\_query\_var( ‘page’ ) if you want this query to work in a Page template that you’ve set as your static front page.

</p>
<?php
/\* Get all Sticky Posts \*/
$sticky = get\_option( 'sticky\_posts' );

/\* Sort Sticky Posts, newest at the top \*/
rsort( $sticky );

/\* Get top 5 Sticky Posts \*/
$sticky = array\_slice( $sticky, 0, 5 );

/\* Query Sticky Posts \*/
$query = new WP\_Query( array( 'post\_\_in' => $sticky, 'ignore\_sticky\_posts' => 1 ) );
?>

<p>

[Expand full source code](#)[Collapse full source code](#)

## Style Sticky Posts

To help theme authors perform simpler styling, the [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) function is used to add class=”…” to DIV, just add:

</p>
<div id="post-<?php the\_ID(); ?>" <?php post\_class(); ?>>

<p>

The [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) outputs the class=”whatever” piece for that div. This includes several different classes of value: post, hentry (for hAtom microformat pages), category-X (where X is the slug of every category the post is in), and tag-X (similar, but with tags). It also adds “sticky” for posts marked as Sticky Posts.

</p>
.sticky { color:red; }
<p>

Note: The “sticky” class is only added for sticky posts on the first page of the home page ([is\_home()](https://developer.wordpress.org/reference/functions/is_home/) is true and [is\_paged()](https://developer.wordpress.org/reference/functions/is_paged/) is false)