# Pagination

Pagination allows your user to *page* back and forth through multiple pages of content.

WordPress can use pagination when:

*   Viewing lists of posts when more posts exist than can fit on one page, or
*   Breaking up longer posts by manually by using the following tag.
    
     <!--nextpage--> 
    

## Using Pagination to Navigate Post Lists

The most common use for pagination in WordPress sites is to break up long lists of posts into separate pages. Whether you’re viewing a category, archive, or default index page for a blog or site, WordPress only shows 10 posts per page by default. Users can change the number of posts that appear on each page on the Reading screen: **Admin > Settings > Reading**.

## Examples

### Loop with Pagination

This simplified example shows where you can add pagination functions for the main loop. Add the functions just before or after the loop.

</p>
<p>&lt;?php if ( have\_posts() ) : ?></p>
<p>	&lt;!-- Add the pagination functions here. --></p>
<p>	&lt;!-- Start of the main loop. --><br />
	&lt;?php while ( have\_posts() ) : the\_post(); ?></p>
<p>	&lt;!-- the rest of your theme's main loop --></p>
<p>	&lt;?php endwhile; ?><br />
	&lt;!-- End of the main loop --></p>
<p>	&lt;!-- Add the pagination functions here. --></p>
<p>&lt;div class=&quot;nav-previous alignleft&quot;>&lt;?php next\_posts\_link( 'Older posts' ); ?>&lt;/div></p>
<p>&lt;div class=&quot;nav-next alignright&quot;>&lt;?php previous\_posts\_link( 'Newer posts' ); ?>&lt;/div></p>
<p>&lt;?php else : ?></p>
<p>&lt;?php \_e('Sorry, no posts matched your criteria.'); ?></p>
<p>&lt;?php endif; ?></p>
<p>

[Expand full source code](#)[Collapse full source code](#)

### Methods for displaying pagination links

Note: When using any of these pagination functions outside the template file with the loop that is being paginated, you must call the global variable $wp\_query.

<br />
function your\_themes\_pagination(){<br />
	global $wp\_query;<br />
	echo paginate\_links();<br />
}<br />

WordPress has numerous functions for displaying links to other pages in your loop. Some of these functions are only used in very specific contexts. You would use a different function on a single post page then you would on a archive page. The following section covers archive template pagination functions. The section after that cover single post pagination.

#### Simple Pagination

**posts\_nav\_link**

One of the simplest methods is [posts\_nav\_link()](https://developer.wordpress.org/reference/functions/posts_nav_link/). Simply place the function in your template after your loop. This generates both links to the next page of posts and previous page of posts where applicable. This function is ideal for themes that have simple pagination requirements.

 posts\_nav\_link(); 

**next\_posts\_link & prev\_posts\_link**

When building a theme, use [next\_posts\_link()](https://developer.wordpress.org/reference/functions/next_posts_link/) and [prev\_posts\_link()](https://developer.wordpress.org/reference/functions/previous_posts_link/). to have control over where the previous and next posts page link appears.

<br />
next\_posts\_link();<br />
previous\_posts\_link();<br />

If you need to pass the pagination links to a PHP variable, you can use [get\_next\_posts\_link()](https://developer.wordpress.org/reference/functions/get_next_posts_link/) and [get\_previous\_posts\_link()](https://developer.wordpress.org/reference/functions/get_previous_posts_link/).

<br />
$next\_posts = get\_next\_posts\_link();<br />
$prev\_posts = get\_previous\_posts\_link();<br />

#### Numerical Pagination

When you have many pages of content it is a better experience to display a list of page numbers so the user can click on any one of the page links rather then having to repeatedly click next or previous posts. WordPress provides several functions for automatically displaying a numerical pagination list.

**For WordPress 4.1+**

If you want more robust pagination options, you can use [the\_posts\_pagination()](https://developer.wordpress.org/reference/functions/the_posts_pagination/) for WordPress 4.1 and higher. This will output a set of page numbers with links to previous and next pages of posts.

the\_posts\_pagination();

**For WordPress prior to 4.1**

If you want your pagination to support older versions of WordPress, you must use [paginate\_links()](https://developer.wordpress.org/reference/functions/paginate_links/).

echo paginate\_links();

#### Pagination Between Single Posts

All of the previous functions should be used on index and archive pages. When you are viewing a single blog post, you must use [prev\_post\_link](https://developer.wordpress.org/reference/functions/previous_post_link/) and [next\_post\_link](https://developer.wordpress.org/reference/functions/next_post_link/). Place the following functions below the loop on your single.php.

<br />
previous\_post\_link();<br />
next\_post\_link();<br />

### Pagination within a post

WordPress gives you a tag that can be placed in post content to enable pagination for that post.

<!--nextpage-->

If you use that tag in the content, you need to ensure that the [wp\_link\_pages](https://developer.wordpress.org/reference/functions/wp_link_pages/) function is placed in your single.php template within the loop.

<br />
&lt;?php if ( have\_posts() ) : ?></p>
<p>	&lt;!-- Start of the main loop. --><br />
	&lt;?php while ( have\_posts() ) : the\_post(); ?></p>
<p>		&lt;?php the\_content(); ?></p>
<p>		&lt;?php wp\_link\_pages(); ?> </p>
<p>	&lt;?php endwhile; ?></p>
<p>&lt;?php endif; ?><br />