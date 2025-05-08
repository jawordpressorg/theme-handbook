# Usage in Templates

When building themes, patterns are not merely reusable sections of blocks that users can add to their content. That is a nice feature, but the true power of patterns is using them directly in your theme’s front-end output.

In this article, you will learn both why and how to include patterns in your theme’s templates and template parts.

## Why use patterns in templates?

There are two primary reasons to use patterns in your templates:

*   **PHP access:** Block templates and template parts are HTML files and you need access to various PHP functions for dynamic functionality. You can learn more about this in the [Using PHP in Patterns](https://developer.wordpress.org/themes/patterns/using-php-in-patterns/) documentation.
*   **The DRY (Don’t Repeat Yourself) principle:** When building any type of software (themes included) you should always reuse code when possible, which means less work for you and fewer potential bugs. Because patterns are reusable groups of blocks, it makes sense to use the pattern instead of rewriting the code in your templates and parts.

This article will primarily focus on the last point. You will learn how to reuse your patterns within your theme’s block templates and template parts.

One of the best use cases is to create patterns of common elements across multiple templates. For example, if your Home, Archive, and Search templates all include the same Query Loop layout, create a pattern for that design and include it in each template.

## The Pattern block

As described in [Introduction to Patterns](https://developer.wordpress.org/themes/patterns/introduction-to-patterns/), a block pattern is merely one or more blocks that you have registered as a pattern. However, there is also a block named Pattern available in WordPress. You won’t find the Pattern block anywhere in the UI (such as the block inserter). It’s primarily meant to be used in WordPress themes.

Here is what the Pattern block markup looks like:

```markup
<!-- wp:pattern {"slug":"namespace/pattern-slug"} /-->
```

As you can see, it looks just like any other block markup. The big difference is that you must set the `slug` parameter to include a specific pattern. The value must include both the pattern namespace and slug.

Whenever you want to include a pattern within a template or template part, you only need to call the Pattern block.

You can also include patterns registered by WordPress or plugins in templates, not just those from your theme. All you need to do is reference the correct `slug` value when calling the Pattern block.

## Adding a pattern to a template

In this section, you will walk through a practical example of including a pattern within a template.

Assume you had a “hero” pattern that you have registered for your theme because you want users to be able to insert it anywhere they need to. But you also want to include this in your Home template by default.

First, register a custom pattern with the `themeslug/hero`, as described in the [Registering Patterns](https://developer.wordpress.org/themes/patterns/registering-patterns/) documentation. Create a new file named `hero.php` and place it into your theme’s `/patterns` folder with this code:

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"overlayColor":"contrast","isUserOverlayColor":true,"align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim-100 has-background-dim"></span>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themeslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

This will make the pattern both available to users via the UI and to your theme templates for inclusion.

To include this specific pattern in a template, you need to call it like so:

```markup
<!-- wp:pattern {"slug":"themeslug/hero"} /-->
```

Now try adding it to one of your theme’s templates, such as `/templates/home.html` or `/templates/index.html` below the header. Your template with the pattern code should look similar to this:

```markup
<!-- wp:template-part {"slug":"header"} /-->

<!-- wp:pattern {"slug":"themeslug/hero"} /-->

<!-- Some other blocks. /-->

<!-- wp:template-part {"slug":"footer"} /-->
```

Now test the addition of the pattern in the Site Editor by going to **Appearance > Editor > Templates** and choosing the template you added it to:

[![WordPress Site Editor with the Home/Blog template open. It shows a Header template part and a "welcome" message in a Cover block at the top of the template.](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/template-home-pattern.webp?ssl=1)

The pattern should also appear on the front end of your site when that template is in use.

From this point, you can use this feature however you need. Whether you’re including a pattern in a template or template part, the process is the same.