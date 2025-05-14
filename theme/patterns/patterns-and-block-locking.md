# Patterns and Block Locking

The [Block Locking API](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) is a powerful set of features that lets you lock the behavior of blocks and how users interact with them. You can control whether users can remove, move, or customize blocks, which lets you further curate the editing experience of your themes.

This article will explore some of the ways that you can utilize the API within your theme’s patterns. But for a deeper dive into the API, please refer to the [Block Locking documentation](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/) in the Block Editor Handbook.

You are not only limited to using Block Locking in patterns. You can also apply the methods in this article to [templates](https://developer.wordpress.org/themes/templates/).

## What is Block Locking?

The Block Locking API lets you control how a user interacts with blocks on their site. The types of locking you can do are:

*   Disabling block movement in the editor.
*   Preventing a block from being removed.
*   Preventing new blocks from being inserted.
*   Disabling editing block settings other than content and media.

This can be really useful depending on the scenario. For example, it often makes sense to lock a site header pattern, which can be complex, by disabling the deletion of its inner blocks by accident.

There are also two types of locking the API offers: block and template. Locking at the block level means preventing the user from taking some actions for the individual block. Locking at the template level means preventing the user from some actions at a “group” level.

It’s important to note that “template” here refers to a section of blocks nested within a container block, such as Group, Cover, etc. It’s not referring specifically to template files.

## Block locking

In this section, you will learn how to lock individual blocks. Namely, preventing a user from moving a block or removing it altogether.

First, you should familiarize yourself with how to lock blocks from the UI. Let’s start by creating a custom “event” pattern to work for throughout the remainder of this article.

Create a new file in your theme named `/patterns/event.php` and place the following code into it:

```php
<?php
/**
 * Title: Event
 * Slug: themeslug/event
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

Then go to the post editor and insert your new pattern. Once you’ve done that, you should see the pattern in the content area.

Now select the Image block (or any block) in the pattern. Then click the **Options** button in the block toolbar. You should see a **Lock** option:

[![WordPress post editor with an event pattern inserted into the content area. The outer Group block is selected and its Options dropdown menu is shown in the toolbar with the "Lock" option highlighted.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-menu.webp?ssl=1)

This will bring up a modal for various locking options, which you’ll learn about in the following sections.

This type of locking is shown in the UI, and a theme user will be able to override it from the UI. For publicly-distributed themes, this is a good thing. But for client work, this type of access may be undesirable. If you need to control permissions to the locking UI, see the instructions in the Locking API docs: [Change permissions to control locking ability](https://developer.wordpress.org/block-editor/how-to-guides/curating-the-editor-experience/block-locking/#change-permissions-to-control-locking-ability).

### Disable block movement

One of the primary use cases of the Block Locking API is to prevent users from accidentally moving blocks around within a pattern, altering the layout. In the **Lock** modal, you will see an option to **Disable movement**. Try selecting this option for the Image block from the event pattern:

[![WordPress post editor with an event pattern inserted into the content area. A "Lock Image" modal overlays the screen with the "Disable movement" option selected.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-disable-movement.webp?ssl=1)

Under the hood, when you select this option, WordPress will add a new `lock` attribute to the block markup that looks like this:

```markup
<!-- wp:image {"lock":{"move":true,"remove":false}} -->
```

Because you’ve selected the **Disable movement** option, the `move` key will have a value of `true` (i.e., movement has been locked).

Now try creating a new version of your pattern with the Image block’s movement disabled. Add a new `/patterns/event-disable-movement.php` file to your theme and paste this code in:

```php
<?php
/**
 * Title: Event (Disable Movement)
 * Slug: themeslug/event-disable-movement
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none","lock":{"move":true,"remove":false}} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

Now, anytime a user adds this pattern to their content, they won’t be able to move the Image block within the pattern.

Just because the Image block’s movement has been disabled, it doesn’t affect other blocks within the pattern. For example, it’s still possible to move the Columns block. You would need to disable both blocks from being moved to stop the user from moving either.

### Prevent block removal

For some patterns, you will want to keep a block from being deleted altogether. For example, in the event pattern, the Image block may be integral to the pattern’s design.

Starting from the original event pattern, repeat the process of opening the **Lock** modal. This time, select the **Prevent removal** option:

[![WordPress post editor with an event pattern inserted into the content area. A "Lock Image" modal overlays the screen with the "Prevent removal" option selected.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal-prevent-removal.webp?ssl=1)

Again, WordPress will automatically insert the `lock` attribute in the block markup, which will look like this:

```markup
<!-- wp:image {"lock":{"move":false,"remove":true}} -->
```

This time, the `remove` option is set to `true` (i.e., removal has been locked).

Now create an alternate version of your pattern with the Image block’s removal disabled. Add a new `/patterns/event-prevent-removal.php` file to your theme and paste this code in:

```php
<?php
/**
 * Title: Event (Prevent Removal)
 * Slug: themeslug/event-prevent-removal
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none","lock":{"move":false,"remove":true}} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

Now, whenever a user inserts this pattern, they will not be able to remove the Image block. They’ll still be able to edit the image itself and any settings, though.

You can combine both of these techniques, locking movement and removal, depending on your use case. For some patterns, this is often needed to keep the design of the pattern intact.

## Template locking

Template locking refers to locking all of the nested blocks within a container-type block. There are three types of locking that you can accomplish with template locking:

*   **`all`:** Combined with the block locking methods covered earlier, lock all blocks within the container.
*   **`insert`:** Prevent users from inserting new blocks within the container.
*   **`contentOnly`:** Lock down all block settings within the container, only allowing the user to edit content (e.g., text and media).

Template locking is only possible for a subset of container-type blocks in Core:

*   Group
*   Cover
*   Columns
*   Column
*   Navigation

### Locking all nested blocks

With the built-in UI controls, you can lock all nested blocks within a pattern if it’s wrapped in one of the supported container-type blocks. 

This type of locking builds off the block locking covered earlier in this article. You can choose to disable movement, prevent removal, or both for all nested blocks.

When clicking on the wrapping Group block inside your event pattern and opening the **Lock** modal, select both the **Disable movement** and **Prevent removal** options. You should also see another option labeled **Apply to all blocks**, which will let you apply these rules to every block inside the Group:

[![WordPress post editor with an event pattern inserted into the content area. A "Lock Group" modal overlays the screen with all locking options selected and applied to nested blocks.](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/lock-modal.webp?ssl=1)

If you look at the underlying block markup, you will see a new `templateLock` attribute, which will be set to `all`. You will also see the `lock` attribute with both `move` and `remove` set to `true`:

```markup
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true}} -->
```

Like with individual block locking, you can mix and match what you want to lock at the template level.

Now create a new file named `/patterns/event-lock-all.php` in your theme and paste the following code into it:

```php
<?php
/**
 * Title: Event (Lock All)
 * Slug: themeslug/event-lock-all
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"all","lock":{"move":true,"remove":true},"align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

Whenever a user inserts this new pattern into their content, they will not be able to move or remove any of the blocks within the pattern. But they can still edit each block’s content and settings.

### Preventing new blocks from being inserted

You can also lock your container-type blocks in patterns from having new blocks inserted into them. This is useful when you need to keep tight control over what is allowed within the design.

Unlock previous methods of locking blocks, this method has no UI controls associated with it. This means that you must edit the block markup directly by adding the `templateLock` value.

Take a look at what this looks like when applied to a wrapping Group block:

```markup
<!-- wp:group {"templateLock":"insert"} -->
```

As you can see, the `templateLock` attribute is set to `insert` (i.e, the Group has locked inserting new blocks).

Now create a new file in your theme named `/patterns/event-prevent-insert.php` and paste the following code into it:

```php
<?php
/**
 * Title: Event (Prevent Insert)
 * Slug: themeslug/event-prevent-insert
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"insert","align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

When a user adds this pattern into their post or page content, they will be able to customize the blocks within the pattern. But they will not be able to add any new blocks from within the UI.

### Applying content-only editing

One of the most useful features for patterns is to use template locking to only allow the user to customize the content of a pattern. This can be useful when you need full control over the design but need to allow user input.

When this type of locking is applied to a container-type block, users will see a new **Content** panel when inspecting any block instead of the usual block settings:

[![WordPress post editor with an event pattern shown. The outer Group block is selected. In the sidebar, instead of the normal design and setting controls, it has a "Content" panel that shows the nested blocks.](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?resize=2048%2C1061&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2024/04/pattern-locking-content-only.webp?ssl=1)

This is also a type of locking that has no UI controls and must be manually applied to the block markup. If applied to the outer Group block of your pattern, it will look like this:

```markup
<!-- wp:group {"templateLock":"contentOnly"} -->
```

Note that the `templateLock` attribute is set to `contentOnly`, which means that everything but content editing is locked.

Now let’s apply this to the event pattern. Create a new file in your theme named `/patterns/event-content-only.php` and paste the following code into it:

```php
<?php
/**
 * Title: Event (Content Only)
 * Slug: themeslug/event-content-only
 * Categories: banner
 * Viewport Width: 1376
 */
?>
<!-- wp:group {"templateLock":"contentOnly","align":"wide","style":{"elements":{"link":{"color":{"text":"var:preset|color|base-2"}}},"spacing":{"padding":{"top":"var:preset|spacing|30","bottom":"var:preset|spacing|30","left":"var:preset|spacing|30","right":"var:preset|spacing|30"}}},"backgroundColor":"contrast","textColor":"base-2","layout":{"type":"default"}} -->
<div class="wp-block-group alignwide has-base-2-color has-contrast-background-color has-text-color has-background has-link-color" style="padding-top:var(--wp--preset--spacing--30);padding-right:var(--wp--preset--spacing--30);padding-bottom:var(--wp--preset--spacing--30);padding-left:var(--wp--preset--spacing--30)">

	<!-- wp:image {"sizeSlug":"full","linkDestination":"none"} -->
	<figure class="wp-block-image size-full"><img src="https://s.w.org/patterns/files/2021/06/Group-17-scaled.jpg" alt="Image of a woman being carried through the air by swans."/></figure>
	<!-- /wp:image -->

	<!-- wp:columns {"verticalAlignment":"center"} -->
	<div class="wp-block-columns are-vertically-aligned-center">
		
		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Location:', 'themeslug' ); ?></strong><br><?php esc_html_e( '82 Main St. Brooklyn, NY', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:paragraph -->
			<p><strong><?php esc_html_e( 'Date:', 'themeslug' ); ?></strong><br><?php esc_html_e( 'October 24, 2021', 'themeslug' ); ?></p>
			<!-- /wp:paragraph -->
		</div>
		<!-- /wp:column -->

		<!-- wp:column {"verticalAlignment":"center"} -->
		<div class="wp-block-column is-vertically-aligned-center">
			<!-- wp:buttons -->
			<div class="wp-block-buttons">
				<!-- wp:button {"width":100,"className":"is-style-outline"} -->
				<div class="wp-block-button has-custom-width wp-block-button__width-100 is-style-outline"><a class="wp-block-button__link wp-element-button"><?php esc_html_e( 'Purchase Tickets' ); ?></a></div>
				<!-- /wp:button -->
			</div>
			<!-- /wp:buttons -->
		</div>
		<!-- /wp:column -->

	</div>
	<!-- /wp:columns -->

</div>
<!-- /wp:group -->
```

With this setting in place, the user will be able to edit the Image block’s media and the content of the individual Paragraph and Button blocks. But they won’t be able to make any design changes directly inside of the pattern.