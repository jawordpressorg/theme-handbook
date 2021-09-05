# 404 Pages

A 404 page is important to add into your theme in case a user stumbles upon a page that doesn’t exist or hasn’t been created yet. It is also important that your 404 page gives your visitors a way to arrive at the right place.

These next few steps will help you build a useful 404 page for your WordPress theme.

## Creating the 404.php file

As the `404.php` file is used on a page not found error, the first step is to create a file named `404.php` and add it to your WordPress theme folder.

Tip: Often times a great starting point for your `404.php` is your `index.php`

## Add a file header

To use your theme’s `header.php` file, open your `404.php` file. At the top, add a comment describing what the file is and make sure you include your theme’s header.

For example:

<br />
/\*\*<br />
 \* The template for displaying 404 pages (Not Found)<br />
 \*/<br />
get\_header();<br />

## Adding the body to your 404 Page

To make the 404 page functional you have to add the body content to your template:

Example:

<br />
&lt;div id=&quot;primary&quot; class=&quot;content-area&quot;><br />
		&lt;div id=&quot;content&quot; class=&quot;site-content&quot; role=&quot;main&quot;></p>
<p>			&lt;header class=&quot;page-header&quot;><br />
				&lt;h1 class=&quot;page-title&quot;>&lt;?php \_e( 'Not Found', 'twentythirteen' ); ?>&lt;/h1><br />
			&lt;/header></p>
<p>			&lt;div class=&quot;page-wrapper&quot;><br />
				&lt;div class=&quot;page-content&quot;><br />
					&lt;h2>&lt;?php \_e( 'This is somewhat embarrassing, isn’t it?', 'twentythirteen' ); ?>&lt;/h2><br />
					&lt;p>&lt;?php \_e( 'It looks like nothing was found at this location. Maybe try a search?', 'twentythirteen' ); ?>&lt;/p></p>
<p>					&lt;?php get\_search\_form(); ?><br />
				&lt;/div>&lt;!-- .page-content --><br />
			&lt;/div>&lt;!-- .page-wrapper --></p>
<p>		&lt;/div>&lt;!-- #content --><br />
	&lt;/div>&lt;!-- #primary --><br />

[Expand full source code](#)[Collapse full source code](#)

This example is from the Twenty Thirteen theme that comes with WordPress. This adds some text and a search form in the 404 page.

Note: You can to add your own text to make your 404 page look better.

## Adding the footer and sidebar.

The final step when creating a 404 page is to add the footer. You may also add a sidebar if you want.

Example:

<br />
get\_sidebar();<br />
get\_footer();<br />

Now you have a functional 404 page with a search form and some text in case a user stumbles upon the wrong page. Once you make sure the `404.php` has been uploaded, you can test your 404 page. Just type a URL address for your website that doesn’t exist. You can try something like `http://example.com/fred.php`. This is sure to result in a 404 error unless you actually have a PHP file called `` fred.php`.` ``