# Taxonomy Templates

When a visitor clicks on a hyperlink to category, tag or custom taxonomy, WordPress displays a page of posts in reverse chronological order filtered by that taxonomy.

By default, this page is generated using the *index.php* template file. You can create optional template files to override and refine the *index.php* template files. This section explains how to use and create such templates.

## Taxonomy Template Hierarchy

WordPress display posts in the order determined by the [Template Hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/ "Template Hierarchy").

The *category.php*, *tag.php*, and *taxonomy.php* templates allow posts **filtered** by taxonomy to be treated differently from **unfiltered** posts or posts **filtered by a different taxonomy**. (Note: post refers to any post type – posts, pages, custom post types, etc.). These files let you target specific taxonomies or specific taxonomy terms. For example:

*   *taxonomy-{taxonomy}-{term}.php*
*   *taxonomy-{taxonomy}.php*
*   *tag-{slug}.php*
*   *tag-{id}.php*
*   *category-{slug}.php*
*   *category-{ID}.php*

So you could format all posts in an animal taxonomy named *news* on a page that looks different from posts filtered in other categories.

The *archive.php* template provides the most general form of control, providing a layout for all archives; that is, a page that displays a list of posts.

### Category

For categories, WordPress looks for the *category-{slug}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *category-{ID}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it reverts to the default behavior, using *index.php*.

The category hierarchy is listed below:

1.  *category-{slug}.php*: For example, if the category’s slug is named “news,” WordPress would look for a file named *category-news.php.*
2.  *category-{ID}.php*: For example, if the category’s ID is “6”, WordPress would look for a file named *category-6.php.*
3.  *category.php*
4.  *archive.php*
5.  *index.php*

### Tag

For tags, WordPress looks for the *tag-{slug}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *tag-{ID}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it will revert to the default behavior, using *index.php*.

The tag hierarchy is listed below:

1.  *tag-{slug}.php*: For example, if the tag’s slug is named “sometag,” WordPress would look for a file named *tag-sometag.php.*
2.  *tag-{id}.php*: For example, if the tag’s ID were “6,” WordPress would look for a file named *tag-6.php*.
3.  *tag.php*
4.  *archive.php*
5.  *index.php*

### Custom Taxonomy

A custom taxonomy hierarchy works similarly to the categories and tags hierarchies described above. WordPress looks for the *taxonomy-{taxonomy}-{term}.php* file. If it doesn’t exist, WordPress then looks for a file for the next hierarchical level, *taxonomy-{taxonomy}.php*, and so on. If WordPress fails to find any specialized templates or an *archive.php* template file, it will revert to the default behavior, using *index.php*.

The hierarchy for a custom taxonomy is listed below:

1.  *taxonomy-{taxonomy}-{term}.php*: For example, if the taxonomy is named “sometax,” and the taxonomy’s term is “someterm,” WordPress would look for a file named *taxonomy-sometax-someterm.php*.
2.  *taxonomy-{taxonomy}.php*: For example, if the taxonomy is named “sometax,” WordPress would look for a file named *taxonomy-sometax.php*
3.  *taxonomy.php*
4.  *archive.php*
5.  *index.php*

## Creating Taxonomy Template Files

Now you’ve decided that you need to create custom designs for content based on taxonomies, where do you start?

Rather than starting from a blank file, it is good practice to **copy the next file in the hierarchy**, if it exists. If you’ve already created an *archive.php*, make a copy called *category.php* and modify that to suit your design needs. If you don’t have an *archive.php* file, use a copy of your theme’s *index.php* as a starting point.

Follow the same procedure if you are creating any taxonomy template file. Use a copy of your *archive.php*, *category.php*, *tag.php*, or *index.php* as a starting point.

## Examples

Now that you’ve selected the template file in your theme’s directory that you need to modify, let’s look at some examples.

### Adding Text to Category Pages

#### Static Text Above Posts

Suppose you want some static text displayed before the list of posts on your category page(s). “Static” is text that remains the same, no matter which posts are displayed below, and no matter which category is displayed.

Open your file and above [The Loop](https://developer.wordpress.org/themes/basics/the-loop/ "The Loop") section of your Template file, insert the following code:

```markup
<p>This is some text that will display at the top of the Category page.</p>
```

This text will only display on an archive page displaying posts in that category.

#### Different Text on Some Category Pages

What if you want to display different text based on the category page that the visitor is using? You could add default text to the main *category.php* file, and create special *category-{slug}.php* files each with their own version of the text, but this would create lots of files in your theme. Instead, you can use [conditional tags](https://developer.wordpress.org/themes/basics/conditional-tags/ "Conditional Tags").

Again, this code would be added before the loop:

```php
<?php if ( is_category( 'Category A' ) ) : ?>
	<p>This is the text to describe category A.</p>
<?php elseif ( is_category( 'Category B' ) ) : ?>
	<p>This is the text to describe category B.</p>
<?php else : ?>
	<p>This is some generic text to describe all other category pages, I could be left blank.</p>
<?php endif; ?>
```

This code does the following:

1.  Checks to see if the visitor has requested Category A. If yes, it displays the first piece of text.
2.  Checks for category B if the user didn’t request category A. If yes, it displays the second piece of text.
3.  Displays the default text, if neither was requested.

#### Display Text only on First Page of Archive

If you have more posts than fits on one page of your archive, the category splits into multiple pages. Perhaps you want to display static text, if the user is on the first page of the results.

To do this, use a PHP if statement that looks at the value of the $paged WordPress variable.

Put the following above The Loop:

```php
<?php if ( $paged < 2 ) : ?>
	<p>Text for first page of Category archive.</p>
<?php endif; ?>
```

This code asks whether the page displayed is the first page of the archive. If it is, the text for the first page is displayed. Otherwise, the text for the subsequent pages is displayed.

### Modify How Posts are Displayed

#### Excerpts vs. Full Posts

You can choose whether to display full posts or just excerpts. By displaying excerpts, you shorten the length of your archive page.

Open your file and find the loop. Look for:

```php
the_content()
```

And replace it with:

```php
the_excerpt()
```

And if your theme is displaying excerpts but you want to display the full content, replace `the_excerpt` with `the_content`.
