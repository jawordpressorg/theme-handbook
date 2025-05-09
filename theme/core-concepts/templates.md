# Templates

In block themes, templates are made up of a collection of blocks. You might have a Site Logo block sitting next to a Navigation block in the header area. You might put Social Icons in the footer above a copyright notice.

As you build out your own themes, you will get to decide how your templates come together. *That’s at least half the fun of theming!*

In this document, you will learn the basic terminology around templating in WordPress. Reading through this quick primer on the subject will provide you with some foundational knowledge moving forward. There is a dedicated [Templates](https://developer.wordpress.org/themes/templates/) chapter that provides a full overview of working with templates.

## What are templates?

Theme templates represent the markup of the webpage. They create the document structure and print both static data (e.g., paragraph text) and dynamic data (e.g., post content) to the front end of your site.

Let’s take a look at a template from the default Twenty Twenty-Three theme.

Go to **Appearance > Editor > Templates > Single Posts** in your WordPress admin. This will show you what a Single post template looks like:

[![WordPress Site Editor with a focus on the Single Post template.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-editor.jpg?ssl=1)

Single post template of the default Twenty Twenty-Three theme.

As shown above, the template is made up of various blocks. Some of them are in placeholder states and will dynamically display content based on what page is being viewed on the front end of the site.

If you select the **⋮ (Options)** button in the template editor and select the **Code editor** option, you will see the block markup of the template:

[![WordPress site editor showing the Single Post template in code view, which shows the block markup.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-single-template-code.jpg?ssl=1)

Code view of the default Twenty Twenty-Three theme’s single post template.

One of the great things about templating in WordPress is that you never really have to interact directly with template code. You have the visual Site Editor to make any and all customizations you want. But the code is there if you need it.

Ultimately, the template produces HTML markup on the front end like this (shortened for clarity):

```markup
<!DOCTYPE html>
<html lang="en-US">
<head>
	<title>Post Title</title>
	<!-- Scripts, styles, and meta here. -->
</head>

<body class="post-template single single-post">
	<div class="wp-site-blocks">
		<header class="wp-block-template-part">
			<!-- Header blocks here. -->
		</header>
		<main class="wp-block-group is-layout-flow wp-block-group-is-layout-flow">
			<!-- Nested blocks here. -->
		</main>
		<footer class="wp-block-template-part">
			<!-- Footer blocks here. -->
		</footer>
	</div>
</body>
</html>
```

WordPress automatically handles the final markup for you, so all you need to do is create the templates.

## How the templating system works

Whenever you visit a page on the front end of your website, WordPress must determine which template file to load. In the example above, the Single post template (`single.html`) is used to display the content of single blog posts.

But there are many other types of templates. For example, you might have a Page template (`page.html`) for displaying the content of your site’s pages or an Author template (`author.html`) for displaying post author archives.

WordPress uses the template hierarchy to determine which template file to load. It is essentially a set of rules that defines which template to use based on the web page being viewed. If a template doesn’t exist, WordPress will continue looking down through the hierarchy until it finds one that does. 

If no specific template is found, it will fall back to the Index template: `index.html`. As you learned in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), this is the minimum required template for a block theme to function.

The [Templates](https://developer.wordpress.org/themes/templates/) chapter covers the hierarchy in full detail. There, you will learn which templates are loaded for each page of a WordPress site.

### Template files

WordPress expects template files to be located under the `/templates` folder in your theme. A typical theme will have several templates, which would be organized like this:

*   `templates/`
    *   `404.html`
    *   `archive.html`
    *   `author.html`
    *   `index.html` (required)
    *   `page.html`
    *   `single.html`
    *   `search.html`

These are some of the common templates you will find a theme:

*   **`index.html`:** The fallback template file. It is required in all themes.
*   **`404.html`:** The 404 template is used when WordPress cannot find a post, page, or other content that matches the visitor’s request.
*   **`archive.html`:** The archive template is used when visitors request posts by archive-type views like category, author, or date and a more-specific template is unavailable.
*   **`author.html`:** The author page template is used whenever a visitor loads an author archive.
*   **`category.html`:** The category template is used when visitors request posts by category.
*   **`page.html`:** The page template is used when visitors request individual pages.
*   **`search.html`:** The search results template is used to display a visitor’s search results.
*   **`single.html`:**  The single post template is used when a visitor requests a single post.
*   **`tag.html`:** The tag template is used when visitors request posts by tag.

This is not an exhaustive list. You will learn the ins and outs of every template file as you dive deeper into the [Templates](https://developer.wordpress.org/themes/templates/) chapter. The goal for now is to give you a baseline understanding of what to expect.

## Template parts

Template parts, or “parts” for short, are another integral part of the templating system in WordPress. As the name suggests, template parts are a “part” of a template.

A template may consist of none, one, or more parts.

The great thing about parts is they help you follow the DRY (Don’t Repeat Yourself) principle. By including parts in your templates, you avoid having to repeat building the same block code over and over.

On most websites, there are sections of the page that typically stay the same, regardless of the page that you are viewing. *Can you think of any repeated sections that are common on websites?*

The site header and footer are likely the most recognizable “parts” of a webpage, and they just so happen to be the most common template parts you’ll find in themes. While it’s not required to include them, they are *de facto* standards.

Go to **Appearance > Editor > Patterns > Template Parts** in your WordPress admin. Here is what the Header template part looks like from the default Twenty Twenty-Three theme:

[![WordPress Patterns library showing Header Template parts.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?resize=2048%2C1066&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-template-parts.jpg?ssl=1)

Headers for the Twenty Twenty-Three theme.

WordPress looks for template parts in your theme’s `/parts` folder, which should be organized like this:

*   `parts/`
    *   `header.html`
    *   `footer.html`

Other common template parts are for the comments area and sidebars, but your theme can have as few or as many parts as you want. 

You’ll learn more about how to register and create custom parts in the [Template Parts](https://developer.wordpress.org/themes/templates/template-parts/) documentation.