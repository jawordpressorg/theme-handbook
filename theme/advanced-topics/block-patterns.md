# Block patterns

Block patterns are predefined block layouts. They provide a means to refine the editorial experience by offering users a preset arrangement of blocks to start building right away.

Do you or your editors find themselves recreating combinations of blocks in the block editor? Then, converting those blocks into a pattern should save some time.

Let’s jump in and learn how you can include them in a theme.

## How to include block patterns

There are two methods for registering or including patterns in your theme and *both approaches are compatible with classic and block themes*:

*   `patterns/` folder (recommended for block themes, [introduced in WordPress 6.0](https://make.wordpress.org/core/2022/05/02/new-features-for-working-with-patterns-and-themes-in-wordpress-6-0/))
*   PHP registration – uses the [`register_block_pattern()`](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#register_block_pattern)

### Using the `patterns/` directory to register patterns

You can add a new `patterns/` directory within the root of your theme and place PHP files within to register patterns. Each individual PHP file would contain a different pattern, e.g. `patterns/my-fun-pattern.php`, `patterns/another-pattern.php`

The following is an example of a simple site footer pattern:

<?php
/\*\*
 \* Title: Footer with text, social links.
 \* Slug: theme-slug/footer-default
 \* Categories: text, site-footer
 \* Block Types: core/template-part/footer
 \* Viewport Width: 1280
 \*/

?>

<!-- wp:group {"align":"full","layout":{"inherit":true}} -->
<div class="wp-block-group alignfull">
	<!-- wp:group {"align":"wide","layout":{"type":"flex","allowOrientation":false,"justifyContent":"space-between"}} -->
	<div class="wp-block-group alignwide">
		<!-- wp:paragraph -->
		<p>&copy; <?php echo esc\_html( gmdate( 'Y' ) ); ?> <?php esc\_html\_e( 'Your Company LLC', 'theme-slug' ); ?> · <a href="#"><?php esc\_html\_e( 'Contact Us', 'theme-slug' ); ?></a></p>
		<!-- /wp:paragraph -->

		<!-- wp:social-links {"className":"is-style-logos-only"} -->
		<ul class="wp-block-social-links has-icon-color is-style-logos-only">
			<!-- wp:social-link {"url":"https://wordpress.org","service":"wordpress"} /-->
		</ul>
		<!-- /wp:social-links -->
	</div>
	<!-- /wp:group -->
</div>
<!-- /wp:group -->

This pattern would be saved in the `patterns/` directory in your theme, e.g. `patterns/footer-default.php`.

The `title` and `slug` properties in the pattern’s header are required. The `title` represents the human-readable name for the pattern, which will show in the pattern inserter. The `slug` represents a unique id for calling the pattern. It is recommended to prefix the slug with your theme’s slug, e.g. `my-theme/my-pattern-slug-name`.

After closing the comment, you can add the block markup as plain text, or you can combine the markup with PHP.

A difference between adding PHP in the block pattern file and adding it in the content of `register_block_pattern()` is that in the pattern file, you need to use `echo`:

<!-- Note the use of echo below. Be mindful when mixing block markup and PHP within your patterns -->
<p>&copy; <?php echo esc\_html( gmdate( 'Y' ) ); ?> <?php esc\_html\_e( 'Your Company LLC', 'theme-slug' ); ?> · <a href="#"><?php esc\_html\_e( 'Contact Us', 'theme-slug' ); ?></a></p>

### PHP registration of block patterns

You can use the [`register_block_pattern()` function](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#register_block_pattern) to register patterns with the [`init`](https://developer.wordpress.org/reference/hooks/init/) hook.

function theme\_slug\_block\_pattern() {
  register\_block\_pattern( ... );
}
 
add\_action( 'init', 'theme\_slug\_block\_pattern' );

The `[register_block_pattern()](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#register_block_pattern)` function requires two properties in order to properly register a custom pattern, along with the `slug`:

*   `title`: A human-readable title for the pattern.
*   `content`: Block HTML Markup for the pattern.
*   `slug`: Represents a unique id for the pattern. It is recommended to prefix the slug with your theme’s slug, e.g. `my-theme/my-pattern-slug-name`.

The following is a minimal example of a pattern with two buttons.

register\_block\_pattern(
    'theme-slug/my-awesome-pattern',
    array(
        'title'       => \_\_( 'Two buttons', 'theme-slug' ),
        'description' => \_x( 'Two horizontal buttons, the left button is filled in, and the right button is outlined.', 'Block pattern description', 'theme-slug' ),
        'categories'  => array( 'theme-slug-custom-category' ),
        'content'     => "<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} --><div class="wp-block-buttons"><!-- wp:button --><div class="wp-block-button"><a class="wp-block-button\_\_link">' . \_\_( 'Go shopping', 'theme-slug' ) . '</a></div><!-- /wp:button --></div><!-- /wp:buttons --></div></div>",
    )
);

You can create patterns of blocks within the block editor and then copy from the code editor, and paste them into the `'content'` property. The `'content'` property contains the markup that your pattern will output when inserted in the block editor.

The `'categories'` property is optional and its value will assign your pattern to either a core or custom pattern category (See: Registering a custom pattern category below).

## Important considerations when creating block patterns

Some key things to keep in mind when you’re creating block patterns in your theme, which we’ll cover:

*   Translations (i18n)
*   Linking assets (images) – use [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/)
*   Copy/pasting patterns from the block editor
*   Including custom CSS classes in your patterns

### Translations (i18n) in patterns

Be sure to include the ability to translate strings when you’re creating your block patterns. For example:

<!-- wp:heading -->
<h2>' . esc\_html\_\_( 'My great heading text', 'theme-slug' ) . '</h2>
<!-- /wp:heading -->

Notice the `esc_html__( 'My great heading text', 'theme-slug' )` in the above code sample. This allows builders to translate your strings into other languages.

The above example would likely be used within the `register_block_pattern()` function. Just be mindful to use `echo` if you’re breaking in and out of plain text and PHP code. If the above code was used within a pattern file (e.g. `pattern/my-pattern.php`) then it would likely be written like this:

<!-- wp:heading -->
<h2><?php echo esc\_html\_\_( 'My great heading text', 'theme-slug' ); ?></h2>
<!-- /wp:heading -->

### Linking assets (images) – use [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/)

If you’re including inline assets in your patterns then you can use the [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) function to point to assets within your theme. Here is an Image block example:

<!-- wp:image {"id":85,"width":750,"height":128,"sizeSlug":"full","linkDestination":"none"} -->
<figure class="wp-block-image size-full"><img src="<?php
echo esc\_url( get\_theme\_file\_uri( 'assets/images/snazzy-cover-image.png' ) ); ?>" alt="Alt text goes here" class="wp-image-85" width="750" height="128"/></figure>
<!-- /wp:image -->

### Copy/pasting patterns from the block editor

A typical workflow for creating block patterns starts in the block editor. You add, group, alter all your blocks and then copy and paste the results into either the `'content' = => 'your content'` if you’re using `register_block_pattern()` function, or just raw if you’re placing in a new PHP file within your `patterns/` directory. You may consider escaping the string before pasting with a tool like: [https://onlinestringtools.com/escape-string](https://onlinestringtools.com/escape-string)

### Including custom CSS classes in your patterns

If you desire to add custom CSS classes to your pattern markup then you will have to use the `className` attribute. For example:

<!-- wp:group {"className":"call-to-action"} -->
<div class="wp-block-group call-to-action">
	<!-- wp:heading {"level":3} -->
	<h3><?php esc\_html\_e( 'My heading', 'theme-slug' ); ?></h3>
	<!-- /wp:heading --></div>
<!-- /wp:group -->

Note the use of `"className":"call-to-action"` *and* within the related, following `<div class="call-to-action">`. Both entries are necessary for this to work.

### Using 3rd-party blocks

It is highly recommended that you conditionally load 3rd-party blocks within your patterns. Otherwise, the experience for rendering patterns can appear broken for end users. Here are two methods for conditionally loading blocks.

#### Conditionally load patterns when using `register_block_pattern()`

Oftentimes, well written plugins offer a parent `class` or `function` for you to check against when relying on its functionality. You can use either the [`function_exists`](https://www.php.net/manual/en/function.function-exists.php) or [`class_exists`](https://www.php.net/manual/en/function.class-exists.php) check within the `init` hook to check and register your pattern using [`register_block_pattern()`](https://developer.wordpress.org/reference/functions/register_block_pattern/), as so:

add\_action( 'init', function() {
    if ( function\_exists( 'some\_plugin\_func' ) ) {
        register\_block\_pattern();
    }
} );

#### Conditionally loading patterns when using `patterns/` directory

Since patterns that are found in the `patterns/` directory are auto-registered then we need to reverse the operation by deregistering it based on if the plugin is active.

For example, if we had `patterns/footer-default.php` in our theme:

<?php
/\*\*
 \* Title: Footer with text, social links.
 \* Slug: theme-slug/footer-default
 \* Categories: text, site-footer
 \* Block Types: core/template-part/footer
 \* Viewport Width: 1280
 \*/

?>

<!-- block markup here -->

If this pattern relied on a 3rd-party block then we would unregister it with [`unregister_block_pattern()`](https://developer.wordpress.org/reference/functions/unregister_block_pattern/), but we would have to hook it to our `init` hook, like so:

add\_action( 'init', function() {
    if ( ! function\_exists( 'some\_plugin\_func' ) ) {
        unregister\_block\_pattern( 'theme-slug/footer-default' );
    }
} );

Alternatively, if there were just a single 3rd-party block amongst many core blocks within a pattern that is loaded through the `patterns/` directory. Then we could use PHP within the pattern to check:

<?php
/\*\*
 \* Title: Footer with text, social links.
 \* Slug: theme-slug/footer-default
 \* Categories: text, site-footer
 \* Block Types: core/template-part/footer
 \* Viewport Width: 1280
 \*/

?>

<!-- some WP core blocks here -->

<?php if ( function\_exists( 'some\_plugin\_func' ) ) : ?>
    <!-- special 3rd-party block is here -->
<?php endif; ?>

<!-- some more WP core blocks here -->

Keep in mind that the pattern will look differently without the block when the 3rd-party block is unavailable and the overall layout may appear broken depending on your styling.

## Registering a custom pattern category

Organizing your block patterns into appropriate categories within the block inserter will help your users quickly find what they need.

You can register a custom category using the [`register_block_pattern_category()`](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#register_block_pattern_category) function. Here is an example:

if ( function\_exists( 'register\_block\_pattern\_category' ) ) {
    register\_block\_pattern\_category(
      'theme-slug-query',
      array( 'label' => \_\_( 'Query', 'theme-slug' ) )
   );
}

This example registers a custom “Query” pattern category, which you can then reference and assign when you’re registering your patterns:

register\_block\_pattern(
	'theme-slug/my-custom-query-pattern',
	array(
         	'categories'  => array( 'theme-slug-query' ),
        ...
        )
);

If you do not assign a category for your block pattern then it will just be automatically assigned to `Uncategorized` in the block inserter.

## Unregister a block pattern category

You can use the [`unregister_block_pattern_category()`](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#unregister_block_pattern_category) helper function to remove previously registered block categories. Typically, you’ll want to call it within the `init` hook, like so:

function theme\_slug\_unregister\_pattern\_categories() {
    unregister\_block\_pattern\_category( 'theme-slug-query' );
}
 
add\_action( 'init', 'theme\_slug\_unregister\_pattern\_categories' );

The `unregister_block_pattern_category()` function accepts one argument: `title`, which is the name of the block pattern category to be unregistered.

## Removing or hiding block patterns

By default, WordPress registers several block patterns and categories. However, theme developers can unregister some or all of these using the following methods:

*   `remove_theme_support( 'core-block-patterns' );` – removes **all** core patterns and should be hooked to either the `init` or the [`after_theme_setup()`](https://developer.wordpress.org/reference/hooks/after_setup_theme/) hooks. Or,
*   [`unregister_block_pattern()`](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/#unregister_block_pattern) – to unregister individual patterns.  
    Example: `unregister_block_pattern( 'core/two-buttons' ); // Removes core two-buttons pattern`

Furthermore, you can disable the calling and displaying of patterns from the WordPress [Block Pattern Directory](https://wordpress.org/patterns/) within you theme by utilizing the [`should_load_remote_block_patterns`](https://developer.wordpress.org/reference/hooks/should_load_remote_block_patterns/) filter.

add\_filter( 'should\_load\_remote\_block\_patterns', '\_\_return\_false' );

## Including block patterns in block theme templates

You can include patterns within your block theme templates by utilizing the Pattern block. Here is an example of how you might include a pattern within your theme’s `templates/front-page.html`

/<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:group {"tagName":"main"} -->
<main class="wp-block-group">

	<!-- wp:pattern {"slug":"theme-slug/collection-cover"} /-->

	<!-- wp:pattern {"slug":"theme-slug/new-product-grid"} /-->

	<!-- wp:pattern {"slug":"theme-slug/collection-side-by-side"} /-->

	<!-- wp:pattern {"slug":"theme-slug/collection-50-50"} /-->

</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer"} /-->

Note the use of the Pattern block’s markup: `<!-- wp:pattern {"slug":"theme-slug/my-neat-pattern"} -->`

## Converting Customizer settings to block patterns

Please see: [Converting Customizer settings to block patterns](https://developer.wordpress.org/themes/block-themes/converting-customizer-settings-to-block-patterns/).

Changelog:

*   **Created** 2022-07-29