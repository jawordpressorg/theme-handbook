# Your First Theme

![getting-started-your-first-theme-01](https://developer.wordpress.org/files/2014/07/getting-started-your-first-theme-01.jpg)

## Required Files

As mentioned earlier in the “[What is a Theme](https://developer.wordpress.org/themes/getting-started/what-is-a-theme/)” section, the *only* files needed for a WordPress theme to work out of the box are an `index.php` file to display your list of posts and a `style.css` file to style the content.

Once you get into more advanced development territory and your themes grow in size and complexity, you’ll find it easier to break your theme into many separate files (called [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template Files")) instead. For example, most WordPress themes will also include:

*   `header.php`
*   `index.php`
*   `sidebar.php`
*   `footer.php`

We will cover creating separate files later in this handbook, but for now let’s get your first theme launched!

(Note: The following steps assume you have already completed the “[Setting up a Development Environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/ "Setting up a Development Environment")” section.)

## Step 1 – Create a theme folder

First, create a new folder on your computer, and name it *my-first-theme*. This is where all of your theme’s files will go.

## Step 2 – Create a style.css file

You can use any basic text editor on your computer to create a new file called style.css.

If you’re on a Windows-based machine use [Notepad](http://en.wikipedia.org/wiki/Notepad_(software)) for now and if you’re using a Mac then use [TextEdit](http://en.wikipedia.org/wiki/TextEdit).

Copy and paste the following code into your newly created `style.css` file:

<br />
/\*<br />
Theme Name: My First WordPress Theme<br />
\*/</p>
<p>body {<br />
background: #21759b;<br />
}<br />

[Reference Gist](https://gist.github.com/philiparthurmoore/0496a9b659c12280666d)

## Step 3 – Create an index.php file

Now create a file named `index.php` and put it into your theme’s folder, adding the following code to it:

<br />
&lt;!DOCTYPE html><br />
&lt;html><br />
&lt;head><br />
&lt;meta charset="&lt;?php bloginfo( 'charset' ); ?>"><br />
&lt;title>&lt;?php wp\_title( '|', true, 'right' ); ?>&lt;/title><br />
&lt;link rel="stylesheet" href="&lt;?php echo esc\_url( get\_stylesheet\_uri() ); ?>" type="text/css" /><br />
&lt;?php wp\_head(); ?><br />
&lt;/head><br />
&lt;body><br />
&lt;h1>&lt;?php bloginfo( 'name' ); ?>&lt;/h1><br />
&lt;h2>&lt;?php bloginfo( 'description' ); ?>&lt;/h2></p>
<p>&lt;?php if ( have\_posts() ) : while ( have\_posts() ) : the\_post(); ?></p>
<p>&lt;h3>&lt;?php the\_title(); ?>&lt;/h3></p>
<p>&lt;?php the\_content(); ?><br />
&lt;?php wp\_link\_pages(); ?><br />
&lt;?php edit\_post\_link(); ?></p>
<p>&lt;?php endwhile; ?></p>
<p>&lt;?php<br />
if ( get\_next\_posts\_link() ) {<br />
next\_posts\_link();<br />
}<br />
?><br />
&lt;?php<br />
if ( get\_previous\_posts\_link() ) {<br />
previous\_posts\_link();<br />
}<br />
?></p>
<p>&lt;?php else: ?></p>
<p>&lt;p>No posts found. :(&lt;/p></p>
<p>&lt;?php endif; ?><br />
&lt;?php wp\_footer(); ?><br />
&lt;/body><br />
&lt;/html><br />

[Expand full source code](#)[Collapse full source code](#)

[Reference Gist](https://gist.github.com/philiparthurmoore/b1f47c15d3eb2c573924)

## Step 4 – Install Your Theme

Copy your new theme into the `wp-content/themes` folder on your development environment and activate it for review and testing.

## Step 5 – Activate Your Theme

Now that you’ve installed your theme, go to **Admin > Appearance > Themes** to activate it.

![getting-started-your-first-theme-02](https://developer.wordpress.org/files/2014/07/getting-started-your-first-theme-02.png)

## Using Your First Theme

**Congratulations – you’ve just made your first WordPress theme!**

If you activate your new theme and view it within a browser, you should see something like this:

![Here's how Your First Theme looks on the front end.](https://developer.wordpress.org/files/2014/07/getting-started-your-first-theme-03.png)

Here’s how Your First Theme looks on the front end.

Okay, so it’s not the *prettiest* theme yet, but it’s a terrific start!

## What have we learned?

Although your first theme may be missing the functionality and design elements that are found in other themes, the basic building blocks of a WordPress theme, as we have just created above, are all the same.

Remember that the key here is *not* to get caught up in how all those other things are done *now*, but to understand the guiding principles behind making WordPress themes that will stand the test of time, no matter how the code changes or the template file structure changes over time.

All websites, regardless of how they are created underneath the hood, need common elements: headers, primary content areas, menus, sidebars, footers, and the like. You’ll find that making WordPress themes is really just another way of crafting a website.

From this most basic theme, you’ll start learning about the building blocks that you put together to create a more complex theme.

## Up Next

In [Chapter 2: Theme Basics](https://developer.wordpress.org/themes/basics/ "Chapter 2: Theme Basics"), we’ll dive further into themes and discuss the templates and other files that make up most themes, along with the PHP used to make dynamic themes, including:

*   Template Tags
*   The Loop
*   Theme Functions
*   Conditional Tags
*   and more