# Templates and template parts

A block template is made up of a list of blocks. Any WordPress block can be used in a template.

Templates are designs for pages and can include one or more template parts.  
Template parts are used to organize a theme in smaller reusable structural parts. They are commonly used for site headers and site footers.

## Block markup

Templates and template parts contain block markup that represents blocks and block settings.  
The block markup differs from standard HTML and uses attributes in JSON format.

In a standard HTML file, you would include an HTML tag, `<head>`, and `<body>`.  
In block themes, these HTML elements are added for you. Necessary PHP hooks that you would add to a classic theme, including `wp_head()`, `wp_body_open()`, and `wp_footer()`, are also added automatically. The markup that is inside the template file is printed between the opening and closing body tags.

A block is added to a template with an HTML comment that includes a prefix, the block name, and optional attributes. In the example below, the source is WordPress, which uses the prefix “wp,” and the block is the site title:

```
<!-- wp:site-title /-->
```

You place block attributes inside the comment, between curly brackets. In this example, the site title is changed from an H1 heading (default) to H2. The heading level of the site title is set to 2:

```
<!-- wp:site-title {"level":2} /-->
```

There are both self-closing and multi-line blocks.  
When adding a heading with custom text, the block markup includes both the HTML comment and the HTML tag. The id is generated automatically to create an anchor to make it easier to link to page sections.

```
<!-- wp:heading {"level":3} -->
<h3 id="hello-world">Hello world</h3>
<!-- /wp:heading -->
```

The closing and opening tag of a block must be placed in the same template. Otherwise, you may encounter block validation errors and your block will not display correctly.

### Adding attributes to the block markup

When you add style attributes to blocks, you must also add these to the HTML tag:

```
"style":{"color":{"text":"#ff7e7e"}}
```

needs to be combined with:

```
style="color:#ff7e7e"
```

Result:

```
<!-- wp:heading {"level":3,"style":{"color":{"text":"#ff7e7e"}}} -->
<h3 class="has-text-color" id="hello-world" style="color:#ff7e7e">Hello world</h3>
<!-- /wp:heading -->
```

### How to find which block markup to use

To get the code for the blocks and block settings, you can add the blocks in the editor and then copy the code from the block toolbar options menu. Paste the code into your template.

[![The Options menu in the block toolbar has a an option for copying the block code.](https://developer.wordpress.org/files/2022/01/toolbar-copy.png)](https://developer.wordpress.org/files/2022/01/toolbar-copy.png)

## Templates

A theme can include different types of templates: Site templates like home, archive, and 404, which are part of the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/) and can be edited in the Site Editor. And page templates that are assigned to a post or page and edited in the template editor.

WordPress saves Templates as a custom post type called `wp_template`.

If WordPress can not find an HTML template file, it will try to find a PHP file in your theme folder and use it as a fallback.

### How to create templates with code

Create a new HTML file for each template and place them inside the templates folder in your theme.  
Add the markup for the blocks you want to display.

### How to create templates in the Site Editor

Please read this support article first if you would like an [introduction to the Site Editor.](https://wordpress.org/support/article/site-editor/)

Only user roles with the correct capabilities (for example, administrator), can access the templates.

The Site Editor’s Templates section displays all editable templates. Both templates from the theme and plugins and user-created page templates.

You can open the list of templates from the Site Editor navigation by clicking on the WordPress icon or Site icon in the top toolbar:

[![The Site Editor Template section has a table that lists all templates.](https://developer.wordpress.org/files/2022/01/FSE-site-editor-template-list.png)](https://developer.wordpress.org/files/2022/01/FSE-site-editor-template-list.png)

From this section, you can use the Add New button to create new templates, with the following conditions:

*   The template must be part of the [template hierarchy](https://developer.wordpress.org/themes/basics/template-hierarchy/)
*   The template does not already exist.

If a template is already listed, click on the template name to edit it. In this view, you can also clear customizations from theme templates and delete user-created templates.

### How to create templates in Template Editing mode

To create new page templates, you need to use the template editing mode instead of the Site Editor.

Please see the article about [How to edit templates via the Post Editor](https://wordpress.org/support/article/template-editor/#how-to-edit-templates-via-the-post-editor).

## Template parts

A Template part is a block type used for structuring your site. It is a container block used to display other blocks, for example, in a site header or site footer. The template part block is available in the block inserter in the template editing mode and the Site Editor.

WordPress saves template parts as a custom post type called `wp_template_part`.

Template parts can use the following attributes:

*   slug: Used to identify the template part
*   theme: The theme slug. Used to identify the template part when the part is placed outside a template, for example in a block pattern.
*   area: Select between uncategorized (general), header and footer
*   tagName: The HTML tag. Select between header, main, section, article, aside, footer and div.

In the editor, template parts support alignments when they are used as inner blocks.

### How to create template parts with code

To manually create template parts with code, you need an HTML file for each template part.  
\-The file does not include the template part block itself but rather the inner blocks, the content inside the template part.

**Example of how to create a header:**

Create a new HTML file called header.html inside your themes `parts` folder.  
Open the file in your code editor and add a group block with a background color:

```
<!-- wp:group {"backgroundColor":"vivid-cyan-blue"} -->
<div class="wp-block-group has-vivid-cyan-blue-background-color has-background"></div><!-- /wp:group -->
```

Set the group block to full width by adding the align attribute: `"align":"full"` and the class name “`alignfull`“:

```
<!-- wp:group {"align":"full","backgroundColor":"vivid-cyan-blue"} -->
<div class="wp-block-group alignfull has-vivid-cyan-blue-background-color has-background"></div>
<!-- /wp:group -->
```

Add some padding so that the inner blocks do not touch the edge of the browser window, using the inner attributes `style`, `spacing`, and `padding`:

```
"style":{"spacing":{"padding":{"top":"2em","right":"2em","bottom":"2em","left":"2em"}}
```

Add the style attribute to the div:

```
style="padding-top:2em;padding-right:2em;padding-bottom:2em;padding-left:2em"
```

Complete code for the group block:

```
<!-- wp:group {"align":"full","style":{"spacing":{"padding":{"top":"2em","right":"2em","bottom":"2em","left":"2em"}}},"backgroundColor":"vivid-cyan-blue"} -->
<div class="wp-block-group alignfull has-vivid-cyan-blue-background-color has-background" style="padding-top:2em;padding-right:2em;padding-bottom:2em;padding-left:2em"></div>
<!-- /wp:group -->
```

Inside the group, add the site title block:

```
<!-- wp:site-title /-->
```

Complete code with the group and site title:

```
<!-- wp:group {"align":"full","style":{"spacing":{"padding":{"top":"2em","right":"2em","bottom":"2em","left":"2em"}}},"backgroundColor":"vivid-cyan-blue"} --><div class="wp-block-group alignfull has-vivid-cyan-blue-background-color has-background" style="padding-top:2em;padding-right:2em;padding-bottom:2em;padding-left:2em"><!-- wp:site-title /--></div><!-- /wp:group -->
```

### How to manually include a template part in a template

To add a template part to a template, add the block markup for the template part block and use the template slug inside the slug attribute.  
If the name of the template part file is header.html, the slug is “header”, and the key- and value pair for the attribute are `"slug":"header"`:

```
<!-- wp:template-part {"slug":"header"} /-->
```

### Adding template parts to theme.json

If you would like the template part to be selectable in the block inserter, you also need to include it in the `templateParts` section of theme.json. The `name` is the slug, the `title` is the visible name in the editor, and the `area` is where you want the part to be displayed.

```
"templateParts": [
	{
		"name": "header",
		"title": "Header",
		"area": "header"
	},
	{
		"name": "footer",
		"title": "Footer",
		"area": "footer"
	}
]
```

### How to create template parts in the Site Editor

The Site Editor’s Template Parts section displays a list of all template parts.  
You can create unlimited template parts using the Add New button. In this view, you can also clear customizations from theme template parts and delete user-created template parts.  
  
When creating the template part, you are asked to enter a name and select between three template part areas: General, header, and footer. Next, the editor opens the template part in isolation. You will only see the template part and not the full template or post content. Add the blocks that you wish to use, and save.

### Template Editing mode

Please see the article on [How to edit templates via the Post Editor](https://wordpress.org/support/article/template-editor/#how-to-edit-templates-via-the-post-editor).

## Changes made in the Site Editor are stored in the database

You can make changes to templates and template parts in two ways: by editing the .html file directly in your code editor, or using the Site Editor.  
Changes that you make in the Site Editor are stored in the database, and are not reflected in the theme’s HTML files. The saved version of the template takes precedence over any changes that you make to the HTML files.

To check if a template has been changed, view the list of templates from the Navigation Sidebar in the Site Editor. Changes are indicated by the blue dot next to the template settings menu:

[![The template list in the Site Editor has a visual indicator in the form of a blue dot, to show that a template has been customized.](https://developer.wordpress.org/files/2022/02/site-editor-change-indicator-59-1024x227.png)](https://developer.wordpress.org/files/2022/02/site-editor-change-indicator-59.png)

To remove the changes made in the Site Editor and display content from the HTML file, select the template settings menu, and choose “Clear customizations”.

Changelog:

*   **Updated** 2022-02-15 Added information about changes in the site editor being saved to the database.
*   **Created** 2022-01-20