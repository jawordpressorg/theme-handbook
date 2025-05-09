# Post Formats

A Post Format is used by a theme for presenting posts in a certain format and style. The Post Formats feature provides a standardized list of formats available to all themes that support the feature. A theme may not support every format on the list; in such a case, it is good form to make this known to users.

A theme cannot introduce formats not on the standardized list, even through plugins. This standardization ensures compatibility between themes and a way for external tools to use the feature in a consistent fashion.

In short, with a theme that supports Post Formats, a blogger can change how a post looks by choosing a Post Format.

Using **Asides** as an example, in the past, a category called Asides was created, and posts were assigned that category, and then displayed differently based on styling rules from [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) or from [in\_category(‘asides’)](https://developer.wordpress.org/reference/functions/in_category/).

With **Post Formats**, the new approach allows a theme to add support for a Post Format (e.g. [add\_theme\_support(‘post-formats’, array(‘aside’))](https://developer.wordpress.org/reference/functions/add_theme_support/)), and then the post format can be selected in the Publish meta box when saving the post. A function call of [get\_post\_format($post->ID)](https://developer.wordpress.org/reference/functions/get_post_format/) can be used to determine the format, and [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) will also create the “format-asides” class, for pure-css styling.

## Supported Formats

The following Post Formats are available, if supported by the theme.

Note that while actual post content won’t change, the theme can display a post differently based on the format chosen. How posts are displayed is entirely up to the theme, but here are some general guidelines on typical uses for the different Post Formats.

*   **aside** – Typically styled without a title. Similar to a Facebook note update.
*   **gallery** – A gallery of images. Post will likely contain a gallery shortcode and will have image attachments.
*   **link** – A link to another site. Themes may wish to use the first <a href=””> tag in the post content as the external link for that post. An alternative approach could be if the post consists only of a URL, then that will be the URL and the title (post\_title) will be the name attached to the anchor for it.
*   **image** – A single image. The first <img /> tag in the post could be considered the image. Alternatively, if the post consists only of a URL, that will be the image URL and the title of the post (post\_title) will be the title attribute for the image.
*   **quote** – A quotation. Probably will contain a blockquote holding the quote content. Alternatively, the quote may be just the content, with the source/author being the title.
*   **status** – A short status update, similar to a Twitter status update.
*   **video** – A single video. The first <video /> tag or object/embed in the post content could be considered the video. Alternatively, if the post consists only of a URL, that will be the video URL. May also contain the video as an attachment to the post, if video support is enabled on the blog (like via a plugin).
*   **audio** – An audio file. Could be used for Podcasting.
*   **chat** – A chat transcript, like so:

```bash
John: foo
Mary: bar
John: foo 2
```

When writing or editing a Post, “Standard” designates that no Post Format is specified. Also if an invalid format is specified, “Standard” (no format) is applied by default.

## Function Reference

### Main Functions

*   [set\_post\_format()](https://developer.wordpress.org/reference/functions/set_post_format/)
*   [get\_post\_format()](https://developer.wordpress.org/reference/functions/get_post_format/)
*   [has\_post\_format()](https://developer.wordpress.org/reference/functions/has_post_format/)

### Other Functions

*   [get\_post\_format\_link()](https://developer.wordpress.org/reference/functions/get_post_format_link/)
*   [get\_post\_format\_string()](https://developer.wordpress.org/reference/functions/get_post_format_string/)

## Adding Theme Support

Themes need to use [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) in the *functions.php* file to tell WordPress which post formats to support by passing an array of formats like so:

```php
<?php
function themename_post_formats_setup() {
	add_theme_support( 'post-formats', array( 'aside', 'gallery' ) );
}
add_action( 'after_setup_theme', 'themename_post_formats_setup' );
```

The [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hook is used so that the post formats support is registered after the theme has loaded.

## Adding Post Type Support

Post Types need to use [add\_post\_type\_support()](https://developer.wordpress.org/reference/functions/add_post_type_support/) in the *functions.php* file to tell WordPress which post formats to support:

```php
<?php
function themename_custom_post_formats_setup() {
	// add post-formats to post_type 'page'
	add_post_type_support( 'page', 'post-formats' );
	// add post-formats to post_type 'my_custom_post_type'
	add_post_type_support( 'my_custom_post_type', 'post-formats' );
}
add_action( 'init', 'themename_custom_post_formats_setup' );
```

Or in the function [register\_post\_type()](https://developer.wordpress.org/reference/functions/register_post_type/), add ‘post-formats’, in ‘supports’ parameter array:

```php
<?php
$args = array(
	'supports' => array( 'title', 'editor', 'author', 'post-formats' ),
);
register_post_type( 'book', $args );
```

[add\_post\_type\_support](https://developer.wordpress.org/reference/functions/add_post_type_support/) should be hooked to [init](https://developer.wordpress.org/reference/hooks/init/) hook, as custom post types may not have been registered at [after\_setup\_theme](https://developer.wordpress.org/reference/hooks/after_setup_theme/).

## Using Formats

In the theme, use [get\_post\_format()](https://developer.wordpress.org/reference/functions/get_post_format/) to check the format for a post, and change its presentation accordingly. Note that posts with the default format will return a value of FALSE. Alternatively, use the [has\_post\_format()](https://developer.wordpress.org/reference/functions/has_post_format/) [conditional tag](https://developer.wordpress.org/themes/basics/conditional-tags/):

```php
<?php
if ( has_post_format( 'video' ) ) {
	echo 'This is the video format.';
}
```

### Suggested Styling

An alternate approach to formats is through styling rules. Themes should use the [post\_class()](https://developer.wordpress.org/reference/functions/post_class/) function in the wrapper code that surrounds the post to add dynamic styling classes. Post formats will cause extra classes to be added in this manner, using the “format-foo” name.

For example, one could hide post titles from status format posts by putting this in your theme’s stylesheet:

```css
.format-status .post-title {
     display: none;
}
```

Each of the formats lend themselves to a certain type of “style”, as dictated by modern usage. It is well to keep in mind the intended usage for each format when applying styles.

For example, the aside, link, and status formats are simple, short, and minor. These will typically be displayed without title or author information. The aside could contain perhaps a paragraph or two, while the link would be only a sentence with a link to a URL in it. Both the link and aside might have a link to the single post page (using [the\_permalink()](https://developer.wordpress.org/reference/functions/the_permalink/)) and would thus allow comments, but the status format very likely would not have such a link.

An image post, on the other hand, would typically just contain a single image, with or without a caption/text to go along with it. An audio/video post would be the same but with audio/video added in. Any of these three could use either plugins or standard [Embeds](https://codex.wordpress.org/Embeds) to display their content. Titles and authorship might not be displayed for them either, as the content could be self-explanatory.

The quote format is especially well suited to posting a simple quote from a person with no extra information. If you were to put the quote into the post content alone, and put the quoted person’s name into the title of the post, then you could style the post so as to display [the\_content()](https://developer.wordpress.org/reference/functions/the_content/) by itself but restyled into a blockquote format, and use [the\_title()](https://developer.wordpress.org/reference/functions/the_title/) to display the quoted person’s name as the byline.

A chat in particular will probably tend towards a monospaced type display, in many cases. With some styling on the .format-chat, you can make it display the content of the post using a monospaced font, perhaps inside a gray background div or similar, thus distinguishing it visually as a chat session.

### Formats in a Child Theme

[Child Themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) inherit the post formats defined by the parent theme. Calling [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/) for post formats in a child theme must be done at a later priority than that of the parent theme and will **override** the existing list, not add to it.

```php
<?php
add_action( 'after_setup_theme', 'childtheme_formats', 11 );
function childtheme_formats() {
	 add_theme_support( 'post-formats', array( 'aside', 'gallery', 'link' ) );
}
```

Calling [remove\_theme\_support(‘post-formats’)](https://developer.wordpress.org/reference/functions/remove_theme_support/) will remove it all together.