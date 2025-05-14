# Templates

Templates are one of the most important aspects of theme development. They are files that you put together to represent the document structure that appears on the front end of a website. When combined with [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) (`theme.json`), you can ultimately create a unique design to use for yourself, clients, or just share with the world.

Templates are how you decide where things are placed within your theme. 

*Want a giant footer at the bottom of the site?* You can do that by adding specific blocks inside a Group block at the bottom of a template.

*Want a sidebar next to the content area?* No problem. You can put a Columns block in one or more of your templates to create that layout.

In [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/), you gained a broad overview of how the WordPress templating system works. In this document, we’ll dive more deeply into the templates themselves.

## How do templates work?

Whenever someone visits any page on your site, WordPress takes a look at the URL, runs some logic under the hood, and figures out what type of page the visitor is looking at. That’s a very simplified explanation of it anyway. For theme development, you don’t need to know *how* this part of the process works too deeply—just what the end result is.

Once WordPress determines the type of page, it runs through its “template loader,” which searches for a template that matches the page type. It does this by attempting to locate templates within the template hierarchy for the page type, which is covered in detail in the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/) documentation.

WordPress will search for templates in the hierarchy in order of priority. If it finds a match in any of these locations, it will stop searching through the hierarchy:

*   User-saved template in the database.
*   Template in a child theme’s `/templates` folder (if child theme is active).
*   Template in the theme’s `/templates` folder.

Once a template is found that matches the page type within the hierarchy, the template is loaded. Its block markup is then parsed and WordPress outputs the resulting HTML markup for the browser to use.

## What’s in a template?

Block theme templates are composed entirely of block markup. That’s it. *Really.*

OK. It’s slightly more nuanced than that. You will generally see these things in block templates:

*   Block markup
*   References to template parts
*   References to block patterns

Ultimately, each of those things is still block markup.

Here’s a look at the `/templates/404.html` template file, which includes all three things:

```markup
<!-- wp:template-part {"slug":"header","tagName":"header"} /-->

<!-- wp:group {"tagName":"main","layout":{"type":"constrained"}} -->
<main class="wp-block-group">
	<!-- wp:pattern {"slug":"twentytwentythree/hidden-404"} /-->
</main>
<!-- /wp:group -->

<!-- wp:template-part {"slug":"footer","tagName":"footer"} /-->
```

Of course, block templates can be much more complex than that. The point is that block templates must consist entirely of block markup for WordPress to correctly parse the code and output it for the browser.

For a more in-depth look at the architecture of a block, check out the [Key Concepts](https://developer.wordpress.org/block-editor/explanations/architecture/key-concepts/) documentation in the Block Editor Handbook.

## Organizing templates

With block themes, there is only one location that you can put block templates: in the theme’s `/templates` folder. It should be structured like this:

*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `home.html`
    *   `index.html` (required)
    *   `page.html`
    *   `singular.html`

The minimum required template file is `index.html`. The existence of this file is how WordPress determines that the theme is a block theme.

Outside of that, you can include as many or as few templates as you need to achieve your theme design.

Technically, WordPress will also look in the `/block-templates` folder if it exists in your theme. This is for backward compatibility with an older version of WordPress. But it is recommended to always use the `/templates` folder instead.

## Building templates

While you can technically type all of the block markup for your templates in your template files, that is not what the typical experience will be when working with block themes. In most cases, you will be working from a visual interface and migrating your block code to your template files.

To explore working with the visual interface, read the support guides on using the Site and Template Editors:

*   [Site Editor](https://wordpress.org/documentation/article/site-editor/)
*   [Template Editor](https://wordpress.org/documentation/article/template-editor/)
    *   [How to edit templates via the Site Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-site-editor)
    *   [How to use the Template Editor via the WordPress Block Editor](https://wordpress.org/documentation/article/template-editor/#how-to-edit-templates-via-the-post-editor)

### Editing templates

To access templates from the WordPress admin, open the **Appearance > Editor** menu in the admin menu. Then click the **Templates** item in the sidebar:

[![WordPress Templates interface in the Site Editor, which shows the template options on the left and preview panel on the right.](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?resize=2048%2C1071&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/templates-site-editor.jpg?ssl=1)

This screen lists all of the existing templates for the site, which can come from three locations:

*   User-created templates saved in the database
*   Templates from the theme’s `/templates` folder
*   Templates dynamically added by plugins

From there, you can make customizations to the existing templates, adjusting blocks to your liking.

Remember that if you save these, they will be stored in the database and will overrule any templates in your theme. If you plan to distribute this theme to others or use it on another site, you must copy the block markup to the matching template in your `/templates` folder as described in [Introduction to Templates](https://developer.wordpress.org/themes/templates/introduction-to-templates/).

### Adding new templates

You can create a new template by clicking the **Add New Template** (**+** icon next to **Templates** heading). This will create a modal overlay as shown here:

[![WordPress Add Template modal overlaid the Site Editor.](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?resize=1600%2C837&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/image.png?ssl=1)

From there, you will be able to create an entirely custom template (if it doesn’t already exist for editing).

Again, any new templates you add via the editor are saved in the database. You must create the template file inside your `/templates` folder and copy the block markup to it if you intend to distribute your theme. Be sure that your template filename matches a valid filename in the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/) (for example, the Home template filename is `home.html`).

### Custom templates

Custom templates are templates that you can assign to individual posts, pages, or entries of a custom post type. They are used for the single post view on the front end of the site.

You or your theme users can select custom templates from the **Template** setting in the **Post/Page** panel in the post editor sidebar:

[![WordPress post editor with the Template option open in the sidebar. The Blank template option is highlighted.](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?resize=2048%2C1068&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/10/post-template.jpg?ssl=1)

This can be a powerful feature that lets you create unique designs for specific circumstances. For example, you could add something as simple as a different layout with a contact form or something as complex as a news-magazine layout with multiple post queries and other sections.

When adding a new template from the **Templates** screen, you can also create a custom template. From the **Add Template** overlay, there is an option named **Custom Template**. By clicking it, you will add a new custom template within your site’s database.

But to distribute your template with your theme, you must add it to a custom template file in your theme’s `/templates` folder.

The great thing about custom templates is that the filename can be anything you want it to be. Just be sure to avoid using the name of a standard template filename from the [Template Hierarchy](https://developer.wordpress.org/themes/templates/template-hierarchy/), so make sure it’s unique.

Because custom templates can be anything, there are no exact rules on what block markup should be included in them. But if you want to display the post or page content, make sure that you’re using the Post Content block somewhere within it.

The only other rule is that you must register your template via your `theme.json` file. How to do this is covered in the [Custom Templates](https://developer.wordpress.org/themes/global-settings-and-styles/custom-templates/) documentation under the [Global Settings and Styles](https://developer.wordpress.org/themes/global-settings-and-styles/) chapter.

Originally, custom templates were called “page templates.” This is because the feature only worked for pages in the initial implementation. Eventually, posts and other custom post types could use the feature, so it was rebranded to “custom templates.” But you may see these referred to as page templates in other documentation or on third-party sites.