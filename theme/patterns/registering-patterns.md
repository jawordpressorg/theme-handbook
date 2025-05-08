# Registering Patterns

In [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/), you learned how to create patterns from the WordPress admin interface. Now it’s time to learn how to add these custom patterns directly to your theme

This article will show you how to take a pattern’s block code and register it with WordPress from within your theme. It will also cover unregistering patterns and registering/unregistering pattern categories.

## Creating patterns

If you’re unfamiliar with creating custom patterns, take a moment to study the [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) guide, which will walk you through the process.

Your pattern can be anything you like, but for the purposes of this article, the code shared below will be of a core Cover block with some blocks nested within it, following this structure:

*   Group
    *   Heading
    *   Paragraph
    *   Buttons
        *   Button

Feel free to try recreating this yourself from the editor, especially if you are just getting used to working with the editor. Here is a screenshot of the pattern from the editor:

[![WordPress pattern editor that shows a basic Cover block with a black background and white demo text in the content area.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-editor.webp?ssl=1)

You can also customize this however you like, but it’s recommended to keep this relatively simple for your first time creating a pattern.

Here is what the above pattern’s block markup looks like (read the [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/) article for more information on getting pattern code):

```markup
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me.  I'll share my likes, hobbies, and more.  Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →︎</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

For the remainder of this article, you will work with this same pattern, learning how to register it, unregister it, and customize it further.

It’s good practice to wrap most patterns in a Group, Cover, or other container block (i.e., a block that allows nested blocks). This makes it easier for your theme users to move the entire pattern around in the editor. You can also add a CSS class to this outer block for any custom styling that applies to the entire pattern.

## Registering patterns

There are two methods for registering block patterns in WordPress:

*   By placing files with block markup in them into the /patterns folder in your theme.
*   By manually calling the `register_block_pattern()` function.

The most straightforward route is the first. You’ll learn how to do both in the next sections, but this handbook will recommend using the `/patterns` folder except in some edge cases.

### Using the /patterns directory to register patterns

WordPress will recognize any pattern file placed in your theme’s `/patterns` folder, and it will automatically register it for you, provided that it has a valid pattern file header.

A [file header](https://codex.wordpress.org/File_Header) is PHP-commented code with a list of key + value pairs at the top of a file. WordPress parses this information to gather metadata. In this case, the metadata is used to register a block pattern.

For pattern file headers, these are the keys that you can set:

*   **`Title`:** A human-readable title that can be translated.
*   **`Slug`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`Categories`:** A comma-separated list of categories in which the pattern belongs.
*   **`Description`:** The long description of the registered pattern. Only shown to screen readers.
*   **`Viewport Width`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
*   **`Inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
*   **`Keywords`:** A comma-separated list of keywords related to the pattern. Used when a user searches in the inserter.
*   **`Block Types`:** A comma-separated list of block types to associate the pattern with (e.g., `core/cover`, `core/post-content`).
*   **`Post Types`:** A comma-separated list of post types in which to limit the pattern (e.g., `post`, `page`). Defaults to all post types.
*   **`Template Types`:** A comma-separated list of template types the pattern fits with (e.g., `home`, `single`).

For most patterns, you should at least add the Title, Slug, and Categories fields. Pattern files should look like this:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- Pattern code goes here. -->
```

Now let’s add the code that you copied from the previous section into the `/patterns/hero.php` file in your theme:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull"><span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span><div class="wp-block-cover__inner-container"><!-- wp:group {"style":{"spacing":{"blockGap":"2.5rem"}},"layout":{"type":"constrained","wideSize":"%","contentSize":"75%"}} -->
<div class="wp-block-group"><!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->

<!-- wp:paragraph {"align":"center"} -->
<p class="has-text-align-center">This is my little home away from home. Here, you will get to know me. I'll share my likes, hobbies, and more. Every now and then, I'll even have something interesting to say in a blog post.</p>
<!-- /wp:paragraph -->

<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
<div class="wp-block-buttons"><!-- wp:button {"className":"is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">See My Popular Posts →︎</a></div>
<!-- /wp:button --></div>
<!-- /wp:buttons --></div>
<!-- /wp:group --></div></div>
<!-- /wp:cover -->
```

Now if you add or edit a new post in WordPress, you should see your pattern listed in the inserter. Click the **Patterns** tab and select **Featured**:

[![WordPress post editor with the Patterns inserter open. The Featured sub-panel is selected and shows a single pattern.](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?resize=2048%2C924&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/patterns-insert-custom.webp?ssl=1)

You should also be able to see your pattern listed under **Appearance > Editor > Patterns** in the WordPress admin.

### Using PHP to register patterns

Instead of using the `/patterns` folder to auto-register your patterns, you may choose to manually register them via PHP. You can mix and match both registration methods, but an individual pattern must be registered with only one method.

To register block patterns with PHP, you must use the [`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/) function. Here is what its signature looks like:

```php
register_block_pattern( 
	string $pattern_name, 
	array $pattern_properties 
): bool
```

The function accepts two parameters and returns `true` or `false`, depending on whether the pattern was successfully registered:

*   **`$pattern_name`:** A namespaced slug that is unique to your pattern in the form of `namespace/pattern-name`.
*   **`$pattern_properties`:**
    *   **`content`:** The block markup for the pattern.
    *   **`title`:** A human-readable title that can be translated.
    *   **`categories`:** An array of categories in which the pattern belongs.
    *   **`description`:** The long description of the registered pattern. Only shown to screen readers.
    *   **`viewportWidth`:** The width of the `<iframe>` viewport when previewing the pattern (in pixels).
    *   **`inserter`:** Whether to show the pattern in the inserter. Defaults to `true`.
    *   **`keywords`:** An array of keywords related to the pattern. Used when a user searches in the inserter.
    *   **`blockTypes`:** An array of block types to associate the pattern with.
    *   **`postTypes`:** An array of post types in which to limit the pattern. Defaults to all post types.
    *   **`source`:** The source for the registered pattern. This should be set to `theme` since the pattern is coming from a theme.
    *   **`templateTypes`:** An array of template types the pattern fits with.

When registering patterns via PHP, you should do so on the `init` hook. Now try registering your custom pattern by adding this code in `functions.php` (be sure to add your custom markup to the `content` property):

```php
add_action( 'init', 'themeslug_register_patterns' );

function themeslug_register_patterns() {
	register_block_pattern( 'themeslug/hero', array(
		'title'      => __( 'Hero', 'themeslug' ),
		'categories' => array( 'featured' ),
		'source'     => 'theme',
		'content'    => '<!-- Block pattern goes here. -->'
	) );
}
```

### Conditionally registering patterns

If you need to conditionally register an entire pattern, there are two methods to choose from, depending on how you prefer to register patterns.

#### Conditionally registering patterns in the /patterns folder

If you have used the auto-registration method of placing your pattern in your theme’s `/patterns` folder, there is no true way to conditionally register it. What you must do in this case is unregister the pattern.

Suppose that you wanted to only make the hero pattern you registered earlier available if the `core/paragraph` block is registered. In a real-world scenario, you’d likely be checking for a third-party block, and the `core/paragraph` block is used only for the sake of this example.

Try this code inside of your `functions.php` file to unregister your previously-registered pattern:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) {
		unregister_block_pattern( 'themeslug/hero' );
	}
}
```

The above code uses the [`WP_Block_Type_Registry`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/) class, which stores all block types that are registered on the server-side with WordPress. Using the class’s [`is_registered()`](https://developer.wordpress.org/reference/classes/wp_block_type_registry/is_registered/) method, you can determine whether a block is registered.

#### Conditionally registering patterns via [register\_block\_pattern()](https://developer.wordpress.org/reference/functions/register_block_pattern/)

If you manually registered your patterns via PHP, you only need to wrap your call to `register_block_pattern()` with your conditional check.

Using the same example as above, try only registering your pattern if the `core/paragraph` block is registered by adding this to `functions.php`:

```php
add_action( 'init', 'themeslug_register_patterns', 999 );

function themeslug_register_patterns() {
	if ( WP_Block_Type_Registry::get_instance()->is_registered( 'core/paragraph' ) ) {
		register_block_pattern( 'themeslug/hero', array(
			'title'      => __( 'Hero', 'themeslug' ),
			'categories' => array( 'featured' ),
			'source'     => 'theme',
			'content'    => '<!-- Block pattern goes here. -->'
		) );
	}
}
```

## Unregistering patterns

There are times when you need to unregister block patterns so that they do not appear in the inserter for users. For example, you may want to remove some of the core WordPress patterns, those added by a parent theme (if you’re building a child theme), or those added by third-party plugins.

When you need to unregister a single block pattern, you’ll use the [`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/) function:

```php
unregister_block_pattern( string $pattern_name ): bool
```

Like when registering patterns, you’ll also want to unregister on the `init` hook. Because patterns are generally (but not always) registered with the default priority `10` on `init`, you’ll want to use a higher priority so that your code runs later.

Try unregistering your custom pattern from earlier by adding this code to your `functions.php` file:

```php
add_action( 'init', 'themeslug_unregister_patterns', 999 );

function themeslug_unregister_patterns() {
	unregister_block_pattern( 'themeslug/hero' );
}
```

### Removing Core patterns

While you can use `unregister_block_pattern()` to unregister individual core WordPress patterns, you can also choose to get rid of all of them by removing support for the core-block-patterns feature.

To remove all core WordPress patterns, add this code to your theme’s `functions.php` file:

```php
add_action( 'after_setup_theme', 'themeslug_remove_core_patterns' );

function themeslug_remove_core_patterns() {
	remove_theme_support( 'core-block-patterns' );
}
```

### Disabling remote patterns

WordPress also automatically loads some patterns remotely from the official [Pattern Directory](https://wordpress.org/patterns/) on WordPress.org. There are some situations where you might not want to load these patterns, such as when they don’t match your theme design. You may also want to opt out of calling a remote API on a site that you’re building for a client. Whatever the case, you can disable this by filtering the [`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) hook.

To disable remote patterns, add this code to your `functions.php` file:

```php
add_filter( 'should_load_remote_block_patterns', '__return_false' );
```

## Pattern categories

WordPress has several block pattern categories that it registers by default:

*   `featured`
*   `about`
*   `audio` (added in WordPress 6.4)
*   `banner`
*   `buttons`
*   `call-to-action`
*   `columns`
*   `contact`
*   `footer`
*   `gallery`
*   `header`
*   `media`
*   `portfolio`
*   `posts`
*   `query` (use `posts` instead)
*   `services`
*   `team`
*   `testimonials`
*   `text`
*   `video` (added in WordPress 6.4)

It’s generally best to use these default categories for your theme. This keeps a consistent UI that users will be accustomed to. But there are times when you may want to add your own categories or even remove those that are already registered.

In this section of the article, you’ll learn how to both register and unregister custom block pattern categories.

### Registering a pattern category

To register a custom category for putting one or more of your patterns into, you must use the [`register_block_pattern_category()`](https://developer.wordpress.org/reference/functions/register_block_pattern_category/) function:

```php
register_block_pattern_category( 
	string $category_name, 
	array $category_properties 
): bool
```

The function accepts two parameters:

*   **`$category_name`:** A unique ID/slug for the category. It’s good practice to prefix this with your theme slug (e.g., `themeslug-category-name`).
*   **`$category_properties`:** An array of properties for defining further data about the category:
    *   **`label`:** A human-readable label/title for the category that may be translated.
    *   **`description`:** A description for the category that may be translated.

Try adding a new custom pattern category for your theme. Add this code to your theme’s `functions.php` file:

```php
add_action( 'init', 'themeslug_register_pattern_categories' );

function themeslug_register_pattern_categories() {
	register_block_pattern_category( 'themeslug/custom', array( 
		'label'       => __( 'Theme Name: Custom', 'themeslug' ),
		'description' => __( 'Custom patterns for Theme Name.', 'themeslug' )
	) );
}
```

Now try adding the `themeslug/custom` category to any block pattern:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured, themeslug/custom
 */
?>
<!-- Your block markup goes here. -->
```

Any registered patterns for this category will now appear in the inserter and under **Appearance > Editor > Patterns** (**Appearance > Patterns** for classic themes):

[![WordPress Pattern library in the Site Editor. It shows a custom category selected, which has a single pattern preview.](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/custom-pattern-category.webp?ssl=1)

### Unregistering a pattern category

To unregister a registered pattern category, you must use the [`unregister_block_pattern_category()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern_category/) function:

```php
unregister_block_pattern_category( string $category_name ): bool
```

The function accepts a single parameter:

*   **`$category_name`:** The name (i.e., slug) of the registered category to unregister.

Try adding this code to your `functions.php` to remove the `themeslug/custom` category you registered in the previous step:

```php
add_action( 'init', 'themeslug_unregister_pattern_categories' );

function themeslug_unregister_pattern_categories() {
	register_block_pattern_category( 'themeslug/custom' );
}
```