# What Is a Theme?

A WordPress theme represents the design of your website. It can control everything from colors, to fonts, to the entire layout. In essence, what you see when viewing the front-end of your site is shaped by the theme.

[![A collage of site designs at an angle.](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?resize=2400%2C1500&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-two-collage.jpg?ssl=1)

Templates from the default Twenty Twenty-Two theme.

There are 1,000s of free WordPress themes in the [WordPress.org Theme Directory](https://wordpress.org/themes/) and even more from third-party directories and shops. Many people and businesses also have bespoke (custom-made) themes for their sites.

## What can themes do?

Themes take the content stored by WordPress and display it in the browser. When you create a WordPress theme, you decide how that content looks and is displayed. There are many options available to you when building your theme. The biggest limit is your imagination. 

As a theme creator, you can:

*   Create different layouts, such as one, two or more columns.
*   Control the typography of the site with custom font choices.
*   Skin the site with any color scheme you want.
*   Put a sidebar on the left or right side of the page. Or, have no sidebar at all.
*   Display featured images alongside posts.

[![The WordPress site editor showing the homepage template with a dotted black background and a three-column grid of posts.](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/twenty-twenty-three-style-variation.jpg?ssl=1)

Editing a Twenty Twenty-Three theme style variation.

The WordPress theming system is incredibly powerful. As with every web design project, a good theme is more than defining a layout or two and a few custom colors. The best themes improve engagement with a website’s content *in addition* to being beautiful.

There really are not many limits to the possibilities. Outside of your imagination, theme creation requires some baseline knowledge, which is covered in the [Reading this handbook](https://developer.wordpress.org/themes/getting-started/reading-this-handbook/) page of this chapter. That’s what this handbook is all about—*teaching you what you need to know to build themes of your own*.

## Theme types

WordPress supports two primary types of themes: **block** and **classic**.

There is also a classic subtype that is called a **hybrid** theme, and you’ll learn about it below, too. But the most important distinction is block vs. classic.

Technically, you can even build your own theming system altogether. That’s outside the scope of this handbook, but it’s at least worth noting that WordPress lets you build pretty much whatever you set your mind to.

### Block themes

Block themes are the modern method of building WordPress themes. They generally follow a standard set of conventions and are built entirely out of blocks. This handbook will primarily focus on building themes using this method because it is the future of the WordPress project.

Block themes rely on HTML-based [block templates](https://developer.wordpress.org/themes/templates/) that contain block markup. Both creators and users can edit the templates in the Site Editor. Users can also customize [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) defined by the theme’s `theme.json` file through the Styles interface. 

It’s also possible to export a theme directly from the Site Editor without touching any code. Technically, you cannot create a new theme from scratch entirely from the editor, but you can modify the templates and styles of an existing theme—in essence, creating a custom theme of your own.

[![WordPress site editor with a single post template that shows a design with a yellow background and black text.](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/site-editor-styles.png?ssl=1)

Editing a theme’s styles in the Site Editor.

### Classic themes

Classic themes use a PHP-based templating system, which is still supported in WordPress today. They are still in wide use because they were built on the theming system that was first introduced in 2005 with the launch of [WordPress 1.5](https://wordpress.org/news/2005/02/strayhorn/). There is a long and deep history of classic theming in WordPress, which continues on. For this reason, the handbook maintains documentation for classic themes in the [Classic Themes](https://developer.wordpress.org/themes/classic-themes/) chapter.

Unlike block themes, classic themes have far fewer standards to adhere to, but there are APIs you can use for specific features. The classic theme creation process also requires some minimal PHP, HTML, and CSS code knowledge, at least.

[![WordPress customizer showing the Twenty Twenty-Two theme. On the left is a list of options, and on the right a preview of the site homepage.](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?resize=2400%2C1255&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/customizer-twenty-twenty.jpg?ssl=1)

Editing the default Twenty Twenty theme styles in the customizer.

### Hybrid themes

Hybrid themes are merely classic themes that have adopted some modern block-related features, such as [global settings and styles](https://developer.wordpress.org/themes/global-settings-and-styles/) or [block template parts](https://developer.wordpress.org/themes/templates/template-parts/). This is a widely agreed-upon term by the community, but it is not an “official” theme type. At the end of the day, hybrids are still classic themes.

## Become familiar with themes

To build a WordPress theme of your own, you should familiarize yourself with how themes work from a user’s viewpoint. Before diving into the creation process, try [installing a theme](https://wordpress.org/documentation/article/work-with-themes/) and playing around with it.

WordPress comes with several default themes, titled *Twenty \[Year\]*, but you should also try other themes from the [Theme Directory](https://wordpress.org/themes/) just to get a feel for the possibilities.

## What are themes made of?

Themes can include many different folders and file types. The list below is non-exhaustive, but it includes some of common things you might see:

*   Templates (`.html` in block themes and `.php` in classic themes)
*   CSS Stylesheets
*   JavaScript
*   PHP
*   Media (images, audio, video, etc.)
*   JSON

You will learn more about the specific folders and files used to create a theme in the next chapter: [Core Concepts](https://developer.wordpress.org/themes/core-concepts).

## What is the difference between themes and plugins?

It is common for there to be overlap between features found in themes and plugins. However, best practices are:

*   Themes control the *presentation* of content.
*   Plugins control the behaviors and features of your site.

Any theme that you create should not add site-critical functionality. Doing so means that a user loses access to that functionality when they change their theme.

For example, say you build a theme with a portfolio feature. Users who build their portfolio with your feature will lose it when they change themes. By leaving critical features to plugins, you make it possible to change the design of a website while its features remain intact.

Remember, some users switch themes often. It is best practice to make sure any functionality their sites require, even if the design changes, is in a separate plugin.