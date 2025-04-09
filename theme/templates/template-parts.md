# Template Parts

[Templates](https://developer.wordpress.org/themes/templates/templates/) represent the top-level document structure for the front end of a website. But ***template parts*** represent smaller sections of content that can be included in one or more templates.

Some common parts are:

*   Header
*   Footer
*   Sidebar
*   Comments

You can have many more parts. These are generally pieces of the design that are reused within multiple top-level templates. Parts are not a requirement for your theme, but they are a nice-to-use feature that lets you better manage your files and code.

In [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/), you learned about the basics of template parts. In this document, you’ll gain a deeper understanding of how they work.

## How do template parts work?

As you learned in the Templates documentation, WordPress locates a top-level template based on which page a visitor is viewing on the website. This located template is then loaded, and WordPress parses the block markup before sending it back to the browser.

Unlike templates, parts are not automatically loaded based on the currently-viewed page. They must be included as a *part* of the top-level template via the [Template Part block](https://wordpress.org/documentation/article/template-part-block/).

The Template Part block’s markup looks like this:

```markup
<!-- wp:template-part {"slug":"your-template-part-slug"} /-->
```

There are more block settings that you can include, but the `slug` property **must** be set to load the correct part. When WordPress encounters the Template Part block markup during its parsing process, it will look for a file named `/parts/your-template-part-slug.html` in your theme folder. If found, it will load the file and parse its block markup.

Let’s look at a simple template that loads both a Header and Footer part:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- Other block markup goes here. -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

As you can see, a `tagName` setting was also included for the Header and Footer parts. This sets the wrapping container elements to `<header>` and `<footer>`, respectively.

If this is the block markup included in a top-level template, WordPress would go through these steps:

1.  Load the `/parts/header.html` file and parse its block markup.
2.  Parse the template’s other block markup.
3.  Load the `/parts/footer.html` file and parse its block markup.

## What’s in a template part?

Template parts in block themes contain block markup and nothing else.

Let’s look at a simple Footer template part that shows a Site Title block and a Paragraph block with a “Powered by WordPress” message. To recreate this, you would add a `/parts/footer.html` file in your theme with this block markup:

```markup
<!-- wp:group {"align":"wide","layout":{"type":"flex","orientation":"vertical","justifyContent":"center"}} -->
<div class="wp-block-group alignwide">
	<!-- wp:site-title {"level":0} /-->

	<!-- wp:paragraph -->
		<p>Powered by WordPress.</p>
	<!-- /wp:paragraph -->
</div>
<!-- /wp:group -->
```

This is merely an example that shows block markup and how it *could* look in a part. Template parts can be even simpler or much more complex, depending on what you want to include in them.

For a more in-depth look at the architecture of a block, check out the [Key Concepts](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) documentation in the Block Editor Handbook.

## Organizing template parts

With block themes, you must put template parts within your theme’s `/parts` folder. It should be structured like this:

*   `parts/`
    *   `comments.html`
    *   `footer.html`
    *   `header.html`
    *   `sidebar.html`

None of those are required. In fact, you don’t even have to include any template parts at all.  
WordPress does not currently [support nested template parts](https://github.com/WordPress/gutenberg/issues/54279). For example, you cannot create a `/parts/header` folder and put multiple header parts within it. All template parts must be placed directly within your theme’s `/parts` folder.

Technically, WordPress will also look in the `/block-template-parts` folder if it exists in your theme. This is for backward compatibility with an older version of WordPress. But it is recommended to always use the `/parts` folder instead.

## Building template parts

It’s possible to manually write the block markup code for all of your template parts. But, in most cases, you will want to work directly within the WordPress admin and its visual editor. Then, migrate the block markup from the editor to your template part files as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).

To explore working with the visual interface, read the support guides on using the Site and Template Editors:

*   [Template Part Block](https://wordpress.org/documentation/article/template-part-block/)
*   [Site Editor](https://wordpress.org/documentation/article/site-editor/)
*   [Template Editor](https://wordpress.org/documentation/article/template-editor/)
    *   [How to edit templates via the Site Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [How to use the Template Editor via the WordPress Block Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)

### Registering template parts

While not required, you should almost always register template parts via `theme.json`. Doing so will ensure that they appear in the user interface for use with the Site and Template editors with nice labels that can be translated.

Registering template parts is covered in the [Template Parts](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/) documentation under the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.

### Editing template parts

To access templates from the WordPress admin, open the **Appearance > Editor** menu in the admin menu. Then click the **Patterns** item in the sidebar and scroll to find the **Template Parts** section:

[![WordPress Template Parts section under the Patterns library in the Site Editor. A Post Meta and Comments part are both shown on the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-site-editor.jpg?ssl=1)

Template Parts are categorized by template part areas (read “Template part areas” section below for more information). Each area lists the parts that are registered for it (note that **General** is the `uncategorized` area).

The template parts shown can come from three locations:

*   User-created template parts saved in the database (these are stored as posts in the `wp_template_part` post type)
*   Template parts from the theme’s `/parts` folder
*   Template parts dynamically added by plugins

From this screen, you can make any customizations you want to the parts, adjusting them to fit your vision.

Remember that if you save the parts from this screen, they will be stored in the database and will overrule any templates in your theme. If you plan to distribute this theme to others or use it on another site, you must copy the block markup to the matching template in your `/parts` folder as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).

### Adding new template parts

You can create a new template by clicking the **+** icon next to **Patterns** heading. This will display a dropdown with several options. Click the **Create template part** option as shown here:

[![WordPress Patterns library. A dropdown is shown with the Create Template Part option highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-dropdown.jpg?ssl=1)

Then a popup modal will appear for you to enter a custom template part name and select its area:

[![WordPress Site Editor with a modal for creating a template part overlaying the screen.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-add-new-modal.jpg?ssl=1)

By default, you can select from the General, Header, and Footer areas (to learn more about creating custom areas, read the “Template part areas” section below).

From the next screen, you will be able to create an entirely custom template part. It can include any blocks that you prefer.

Again, any new parts you add via the editor are saved in the database. You must create the template part file inside your `/parts` folder and copy the block markup to it if you intend to distribute your theme.

## Template part areas

Template part areas are essentially a way to organize similar template parts. They also appear as navigational elements within the user interface. Below, you can see the **Header** area highlighted in the template-editing sidebar:

[![WordPress site editor showing a template with a three-column grid of posts. In the sidebar, the Header area is selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-area-navigation.jpg?ssl=1)

By default, WordPress has three areas that you can register your templates for:

*   `uncategorized` (labeled as **General** in the admin)
*   `header`
*   `footer`

That will cover some common use cases (almost all themes need a header and footer, for example). But you may want to create custom areas for your themes to better organize your template parts and provide a nicer user experience.

### Registering custom areas

You can register as many custom areas you want by adding a filter to the [`default_wp_template_part_areas` hook](https://developer.wordpress.org/reference/hooks/default_wp_template_part_areas/). Your callback function accepts a single parameter of `$areas`, which must be an array of area definitions. Each area definition must be an array with these key/value pairs defined:

*   **`area`:** The machine-readable slug for your template part area.
*   **`area_tag`:** The wrapping HTML tag to use for template parts assigned to this area. Can be one of the following:
    *   `div`
    *   `article`
    *   `aside`
    *   `footer`
    *   `header`
    *   `main`
    *   `section`
*   **`label`:** A human-readable label for your area, which may be translated.
*   **`description`:** A description of your area and what template parts belong to it, which may be translated.
*   **`icon`:** The icon to use for the area. Note that only `header`, `footer`, and `sidebar` are currently supported with everything else falling back to a default icon, at least until [this ticket is addressed](https://github.com/WordPress/gutenberg/issues/36814).

Suppose you wanted to create an area named Loop to assign template parts used throughout your theme. You could do so by adding this code to your theme’s `functions.php` file:

```php
add_filter( 'default_wp_template_part_areas', 'themeslug_template_part_areas' );

function themeslug_template_part_areas( array $areas ) {
	$areas[] = array(
		'area'        => 'loop',
		'area_tag'    => 'section',
		'label'       => __( 'Loop', 'themeslug' ),
		'description' => __( 'Custom description', 'themslug' ),
		'icon'        => 'layout'
	);

	return $areas;
}
```

This would register a new Loop area for your theme, but for it to be useful, you need to also register at least one template part for it as described in the [`theme.json` documentation on registering template parts](https://developer.wordpress.org/themes/global-settings-and-styles/template-parts/).

Suppose you also created a `/parts/loop-default.html` template part. You could assign it to your new `loop` area in `theme.json` with this code:

```json
{
	"version": 2,
	"templateParts": [
		{
			"area": "loop",
			"name": "loop-default",
			"title": "Loop - Default"
		}
	]
}
```

This screenshot shows what the **Loop** area would look like in the Site Editor:

[![Template Parts section in the Patterns library in the WordPress Site Editor. A custom Loop template part area is selected.](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/parts-custom-area.jpg?ssl=1)

You can register as many template parts for an area as you need via `theme.json`. For example, you could register a `loop-home.html` and `loop-author.html` to use in your Home and Author templates, respectively. But these are mere examples. The only limit is your imagination.

There are many reasons you might want to register custom areas. For a deeper dive into the benefits and features of this system, read [Upgrading the site-editing experience with custom template part areas](https://developer.wordpress.org/news/2023/06/upgrading-the-site-editing-experience-with-custom-template-part-areas/) from the WordPress Developer Blog.