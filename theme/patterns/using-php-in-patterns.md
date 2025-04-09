# Using PHP in Patterns

One of the biggest advantages of patterns over features like templates and template parts is that you can use PHP in them, which opens a world of possibilities for what you can accomplish. However, there are limits on what functionality is available to your patterns.

In this article, you will learn the limitations of the patterns system, when and how you can use PHP, and some of the most common use cases for dynamic functionality.

## Patterns are registered on init

When using PHP in patterns, it’s important to understand when the pattern’s block markup is actually compiled versus when it is rendered.

Pattern registration happens on the [`init`](https://developer.wordpress.org/reference/hooks/init/) hook. At this point, WordPress compiles the content of the pattern and saves a copy of it as HTML-based block markup. This allows it to be used in both the editor and the front end. It’s during this registration process where the pattern can execute PHP code.

A pattern’s block markup is not actually rendered until it is used either in the editor or on the front end. However, the block markup is plain HTML at the time it is rendered.

At a practical level, this means that a lot of data is unavailable during the registration process on `init`. Your patterns cannot access things like the global query or post. They also cannot use functions associated with that data. So this means that WordPress functions like `is_home()`, `is_single()`, `get_post()`, and others are simply not ready yet.

For example, this PHP wouldn’t execute correctly in a pattern:

```php
<?php if ( is_page() ) : ?>
	<!-- wp:paragraph -->
	<p><?php the_title(); ?></p>
	<!-- /wp:paragraph -->
<?php endif; ?>
```

Neither the `is_page()` nor the `the_title()` functions have the global data they need when a pattern is registered, so they won’t work.

If you’re accustomed to building classic themes, this can feel very unintuitive, especially if you’ve been equating PHP-based patterns to classic, PHP-based template parts.

There are other methods for executing PHP at the time of render, such as using the [Block Bindings API](https://developer.wordpress.org/news/tag/block-bindings/). But those methods are outside the scope of pattern documentation.

You still have a wide and wonderful range of PHP functions and many WordPress functions available to you. And you’ll learn more about what you *can* use in the upcoming sections of this article.

## An example pattern

For the rest of this article, let’s use a single pattern that begins as mostly HTML. Then, you’ll walk through adding PHP to dynamically handle some portions of it. 

Create a new file named `patterns/hero.php` in your theme and put this code into it:

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
		<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center">This is my little home away from home.</p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">Button A</a></div>
			<!-- /wp:button -->
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button">Button B</a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

If you insert it the pattern into the editor, it should look like this:

[![WordPress post editor with a "Welcome to My Site" message in white text with a black background. It is wrapped in a Cover block.](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-default.jpg?ssl=1)

## Internationalizing text in patterns

One of the primary use cases for block patterns is [internationalizing text](https://developer.wordpress.org/themes/functionality/internationalization/) (making it ready for translation). For example, if you have text in a template or template part, the only way to internationalize that text is to move it into a pattern, where you have full access to PHP.

Because pattern files are just PHP, you can use any of the internationalization functions within WordPress. In the below example, you’ll use [`esc_html_e()`](https://developer.wordpress.org/reference/functions/esc_html_e/) to both escape the text for security and make it ready for translators.

Let’s look at the Heading block from your Hero pattern:

```markup
<!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center">Welcome to My Site</h2>
<!-- /wp:heading -->
```

As you can see, the “Welcome to My Site” text in the Heading block is not internationalized. When shipping your theme to users all around the world who speak many different languages, it’s important to ensure this text can be translated.

To internationalize the Heading block’s text, you must wrap it in an internationalization function (`esc_html_e()` in this case). So you’d change the block markup to look like this:

```php
<!-- wp:heading {"textAlign":"center"} -->
<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
<!-- /wp:heading -->
```

There are three other places where you should also make these changes. The first is to the Paragraph block text, and then the two Button blocks. Your new `patterns/hero.php` file should look like this:

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
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

## Using images and other assets

Adding dynamic URLs for images and other assets is another important feature of patterns. Because you have PHP access, you can use functions like [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/) to output an image URL that’s bundled with your theme, for example.

Try adding an image background to your “hero” pattern’s Cover block. If you need an image, try grabbing one from the WordPress [Photo Directory](https://wordpress.org/photos/) (the example below uses this [Nepal night scene photo](https://wordpress.org/photos/photo/41664fab9b/)). 

Download an image and save it to your theme’s `/assets/images` folder (or a folder of your choice) and name it `hero-background.jpg`.

Then open your pattern in the editor and upload the image as the background for the Cover block in your Hero pattern, which should look like this:

[![WordPress post editor with a Cover block that has a background image of a nighttime city. There is a welcome message and buttons overlaying the background.](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?resize=2048%2C1060&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/php-pattern-dynamic-background.webp?ssl=1)

If you copy the blocks that make up the pattern, you’ll notice that you have two instances of the image URL in your pattern code. It will be a hardcoded URL similar to this:

```markup
http://localhost/wp-content/uploads/2023/10/hero-background.jpg
```

You need to change both of those instances so that they point to the image that is located in your theme’s `/assets/images` folder. For this, you need do two things:

*   Get the correct URL using a function like [`get_theme_file_uri()`](https://developer.wordpress.org/reference/functions/get_theme_file_uri/).
*   Escape the URL so that it’s safe for output with [`esc_url()`](https://developer.wordpress.org/reference/functions/esc_url/).

Change the hard coded image URLs to this:

```php
<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>
```

Your final pattern code should look like this (note that this example includes internationalized text as explained in the previous section):

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */
?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span>
	<img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>" data-object-fit="cover"/>
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
			<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
			<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
			<!-- /wp:button -->
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

## foreach() loops

You have access to nearly every PHP function and feature at your disposal, and many things will undoubtedly be useful to you as you build themes. But `foreach()` loops are likely one of the features that you will often reach for.

`foreach()` loops are particularly useful in patterns that have repeated blocks. For example, in your `patterns/hero.php` file, you have a set of two Button blocks:

```php
<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button A', 'themeslug' ); ?></a></div>
<!-- /wp:button -->

<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Button B', 'themeslug' ); ?></a></div>
<!-- /wp:button -->
```

One of the foundational principles of development is DRY (Don’t Repeat Yourself). And this code breaks that principle. With a single `foreach()` loop, you can create the block markup once and loop through it.

First, you need an array of items to loop through, which is the Button content itself. At the top of your `patterns/hero.php` file before the closing `?>` tag, add an array of labels:

```php
$buttons = array(
	__( 'Button A', 'themeslug' ),
	__( 'Button B', 'themeslug' )
);
```

Then replace the markup for your two Button blocks with this code:

```php
<?php foreach ( $buttons as $button ) : ?>
	<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
	<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php echo esc_html( $button ); ?></a></div>
	<!-- /wp:button -->
<?php endforeach; ?>
```

Your full `patterns/hero.php` file should now look like the following (note this includes both the internationalized text and dynamic image example code from earlier):

```php
<?php
/**
 * Title: Hero
 * Slug: themeslug/hero
 * Categories: featured
 */

$buttons = array(
	__( 'Button A', 'themeslug' ),
	__( 'Button B', 'themeslug' )
);

?>
<!-- wp:cover {"url":"<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>","id":3838,"dimRatio":50,"overlayColor":"contrast","align":"full"} -->
<div class="wp-block-cover alignfull">
	<span aria-hidden="true" class="wp-block-cover__background has-contrast-background-color has-background-dim"></span>
	<img class="wp-block-cover__image-background wp-image-3838" alt="" src="<?php echo esc_url( get_theme_file_uri( 'assets/images/hero-background.jpg' ) ); ?>" data-object-fit="cover"/>
	<div class="wp-block-cover__inner-container">
		
		<!-- wp:heading {"textAlign":"center"} -->
		<h2 class="wp-block-heading has-text-align-center"><?php esc_html_e( 'Welcome to My Site', 'themeslug' ); ?></h2>
		<!-- /wp:heading -->

		<!-- wp:paragraph {"align":"center"} -->
		<p class="has-text-align-center"><?php esc_html_e( 'This is my little home away from home.', 'themslug' ); ?></p>
		<!-- /wp:paragraph -->

		<!-- wp:buttons {"layout":{"type":"flex","justifyContent":"center"}} -->
		<div class="wp-block-buttons">
			<?php foreach ( $buttons as $button ) : ?>
				<!-- wp:button {"className":"wp-block-button is-style-outline"} -->
				<div class="wp-block-button is-style-outline"><a class="wp-block-button__link wp-element-button"><?php echo esc_html( $button ); ?></a></div>
				<!-- /wp:button -->
			<?php endforeach; ?>
		</div>
		<!-- /wp:buttons -->

	</div>
</div>
<!-- /wp:cover -->
```

At this point, your pattern is fully dynamic. As you dive deeper into pattern development, you’ll come up with even more use cases for using PHP. Think of this article as just the foundation that you’ll build from.