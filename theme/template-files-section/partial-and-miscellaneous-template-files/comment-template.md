# Comment Template

WordPress displays comments in your theme based on the settings and code in the `comments.php` file within your WordPress theme.

## Simple comments loop

//Get only the approved comments
$args = array(
    'status' => 'approve'
);

// The comment Query
$comments\_query = new WP\_Comment\_Query;
$comments = $comments\_query->query( $args );

// Comment Loop
if ( $comments ) {
 foreach ( $comments as $comment ) {
 echo '<p>' . $comment->comment\_content . '</p>';
 }
} else {
 echo 'No comments found.';
}

The `comments.php` template contains all the logic needed to pull comments out of the database and display them in your theme.

Before we explore the template file you’ll want to know how to pull in the partial template file on the appropriate pages such as `single.php`. You’ll wrap the comment [template tag](https://developer.wordpress.org/themes/basics/template-tags/) in a conditional statement so comments.php is only pulled in if it makes sense to do.

// If comments are open or we have at least one comment, load up the comment template.
 if ( comments\_open() || get\_comments\_number() ) :
     comments\_template();
 endif;

![functionality-comments-01](https://developer.wordpress.org/files/2014/10/functionality-comments-01.png)

## Another Comments.php Example

Here’s an example of the `comments.php` template included with the Twenty Thirteen theme:

<?php
/\*\*
 \* The template for displaying Comments.
 \*
 \* The area of the page that contains comments and the comment form.
 \*
 \* @package WordPress
 \* @subpackage Twenty\_Thirteen
 \* @since Twenty Thirteen 1.0
 \*/

/\*
 \* If the current post is protected by a password and the visitor has not yet
 \* entered the password we will return early without loading the comments.
 \*/
if ( post\_password\_required() )
	return;
?>

<div id="comments" class="comments-area">

	<?php if ( have\_comments() ) : ?>
		<h2 class="comments-title">
			<?php
				printf( \_nx( 'One thought on "%2$s"', '%1$s thoughts on "%2$s"', get\_comments\_number(), 'comments title', 'twentythirteen' ),
					number\_format\_i18n( get\_comments\_number() ), '<span>' . get\_the\_title() . '</span>' );
			?>
		</h2>

		<ol class="comment-list">
			<?php
				wp\_list\_comments( array(
					'style'       => 'ol',
					'short\_ping'  => true,
					'avatar\_size' => 74,
				) );
			?>
		</ol><!-- .comment-list -->

		<?php
			// Are there comments to navigate through?
			if ( get\_comment\_pages\_count() > 1 && get\_option( 'page\_comments' ) ) :
		?>
		<nav class="navigation comment-navigation" role="navigation">
			<h1 class="screen-reader-text section-heading"><?php \_e( 'Comment navigation', 'twentythirteen' ); ?></h1>
			<div class="nav-previous"><?php previous\_comments\_link( \_\_( '&larr; Older Comments', 'twentythirteen' ) ); ?></div>
			<div class="nav-next"><?php next\_comments\_link( \_\_( 'Newer Comments &rarr;', 'twentythirteen' ) ); ?></div>
		</nav><!-- .comment-navigation -->
		<?php endif; // Check for comment navigation ?>

		<?php if ( ! comments\_open() && get\_comments\_number() ) : ?>
		<p class="no-comments"><?php \_e( 'Comments are closed.' , 'twentythirteen' ); ?></p>
		<?php endif; ?>

	<?php endif; // have\_comments() ?>

	<?php comment\_form(); ?>

</div><!-- #comments -->

## Breaking down the comments.php

The above `comments.php` can be broken down to the below parts for better understanding.

1.  [Template Header](#template-header)
2.  [Comments Title](#comments-title)
3.  [Comment Listing](#comment-listing)
4.  [Comment Pagination](#comment-pagination)
5.  [Comments are closed message](#comments-are-closed-message).
6.  [The End](#the-end)

### Template Header

This template begins by identifying the template.

<?php
/\*\*
 \* The template for displaying Comments.
 \*
 \* The area of the page that contains comments and the comment form.
 \*
 \* @package WordPress
 \* @subpackage Twenty\_Thirteen
 \* @since Twenty Thirteen 1.0
 \*/

Next, there’s a test to see if the post is password protected and, if so, it stops processing the template.

/\*
 \* If the current post is protected by a password and the visitor has not yet
 \* entered the password we will return early without loading the comments.
 \*/
if ( post\_password\_required() )
 return;
?>

Finally, there’s a test to see if there are comments associated with this post.

<div id="comments" class="comments-area">

	<?php if ( have\_comments() ) : ?>

### Comments Title

Prints out the header that appears above the comments.

Note: Uses the [](https://developer.wordpress.org/reference/functions/_nx/)[\_nx()](https://developer.wordpress.org/reference/functions/_nx/) translation function so other developers can provide alternative language translations.

<h2 class="comments-title">
			<?php
				printf( \_nx( 'One thought on "%2$s"', '%1$s thoughts on "%2$s"', get\_comments\_number(), 'comments title', 'twentythirteen' ),
					number\_format\_i18n( get\_comments\_number() ), '<span>' . get\_the\_title() . '</span>' );
			?>
		</h2>

### Comment Listing

The following snippet creates an ordered listing of comments using the [wp\_list\_comments()](https://developer.wordpress.org/reference/functions/wp_list_comments/) function.

<ol class="comment-list">
			<?php
				wp\_list\_comments( array(
					'style'       => 'ol',
					'short\_ping'  => true,
					'avatar\_size' => 74,
				) );
			?>
		</ol><!-- .comment-list -->

### Comment Pagination

Checks to see if there are enough comments to merit adding comment navigation and, if so, create comment navigation.

		<?php
			// Are there comments to navigate through?
			if ( get\_comment\_pages\_count() > 1 && get\_option( 'page\_comments' ) ) :
		?>
		<nav class="navigation comment-navigation" role="navigation">
			<h3 class="screen-reader-text section-heading"><?php \_e( 'Comment navigation', 'twentythirteen' ); ?></h3>
			<div class="nav-previous"><?php previous\_comments\_link( \_\_( '&larr; Older Comments', 'twentythirteen' ) ); ?></div>
			<div class="nav-next"><?php next\_comments\_link( \_\_( 'Newer Comments &rarr;', 'twentythirteen' ) ); ?></div>
		</nav><!-- .comment-navigation -->
		<?php endif; // Check for comment navigation ?>

### Comments are closed message.

If comments aren’t open, displays a line indicating that they’re closed.

		<?php if ( ! comments\_open() && get\_comments\_number() ) : ?>
		<p class="no-comments"><?php \_e( 'Comments are closed.' , 'twentythirteen' ); ?></p>
		<?php endif; ?>

### The End

This section ends the comments loop, includes the comment form, and closes the comment wrapper.

	<?php endif; // have\_comments() ?>

	<?php comment\_form(); ?>

</div><!-- #comments -->

## Comments Pagination

If you have a lot of comments (which makes your page long), then there are a number of potential benefits to paginating your comments. Pagination helps improve page load speed, especially on mobile devices.  
Enabling comments pagination is done in two steps.

1.  Enable paged comments within WordPress by going to *Settings* > *Discussion* , and checking the box “*Break comments into pages*” . You can enter any number for the “*top level comments per page*”.
2.  Open your `comments.php` template file and add the following line where you want the comment pagination to appear.

<div class="pagination">
    <?php paginate\_comments\_links(); ?>
</div>

## Alternative Comment Template

On some occasions you may want display your comments differently within your theme. For this you would build an alternate file (ex. short-comments.php) and call it as follows:

 <?php comments\_template( '/short-comments.php' ); ?> 

The path to the file used for an alternative comments template should be relative to the current theme root directory, and include any subfolders. So if the custom comments template is in a folder inside the theme, it may look like this when called:

<?php comments\_template( '/custom-templates/alternative-comments.php' ); ?>

## Function Reference

*   [wp\_list\_comments()](https://developer.wordpress.org/reference/functions/wp_list_comments/) : Displays all comments for a post or Page based on a variety of parameters including ones set in the administration area.
*   [comment\_form()](https://developer.wordpress.org/reference/functions/comment_form/) : This tag outputs a complete commenting form for use within a template.
*   [comments\_template()](https://developer.wordpress.org/reference/functions/comments_template/) : Load the comment template specified in first argument
*   [paginate\_comments\_links()](https://developer.wordpress.org/reference/functions/paginate_comments_links/) : Create pagination links for the comments on the current post.
*   [get\_comments()](https://developer.wordpress.org/reference/functions/get_comments/) : Retrieve the comments with possible use of arguments
*   [get\_approved\_comments()](https://developer.wordpress.org/reference/functions/get_approved_comments/) : Retrieve the approved comments for post id provided.

## Functions reference for retrieving comments meta

*   [get\_comment\_link()](https://developer.wordpress.org/reference/functions/get_comment_link/)
*   [get\_comment\_author()](https://developer.wordpress.org/reference/functions/get_comment_author/)
*   [get\_comment\_date()](https://developer.wordpress.org/reference/functions/get_comment_date/)
*   [get\_comment\_time()](https://developer.wordpress.org/reference/functions/get_comment_time/)
*   [get\_comment\_text()](https://developer.wordpress.org/reference/functions/get_comment_text/)