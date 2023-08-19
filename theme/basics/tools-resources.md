# Tools &amp; Resources

Whether you’re building your very first theme or your tenth, the following resources are meant to help ease the process. Keep in mind that there are various community tools not mentioned here as well but that still might aid in your efforts. 

## Block themes

A block theme is a type of WordPress theme built using blocks. You can read more about these themes in the [Block Theme section](https://developer.wordpress.org/themes/block-themes/).

[**Create Block Theme plugin**](https://wordpress.org/plugins/create-block-theme/) 

This plugin was created by various community members. This tool can create standalone block themes and child themes, depending on your needs. Here are the high-level steps: 

1.  Install and activate the [Create Block Theme](https://github.com/WordPress/create-block-theme) plugin. You will also need to be running the latest version of the [Gutenberg](https://wordpress.org/plugins/gutenberg/) plugin.
2.  Make changes to your site design using the Customizer and Site Editor.
3.  Edit your templates using the Site Editor. For some things, you might need to edit the template files again later.
4.  In the WordPress Admin Dashboard, under Appearance there will be a new page called “Create Block Theme”. You can add the details for the theme here. These details will be used in the style.css file. 
5.  Click the “Create Block Theme” button. From there, a zip file will be downloaded which will contain all the files for your theme.

[**Theme Generator**](https://fullsiteediting.com/block-theme-generator/)

This tool was created by Carolina Nymark and it allows you to create three different types of themes to start from:

*   No Code: for non-developers who want to start from a blank theme and build directly in the Site Editor.
*   Empty: for developers to make their own with six templates and a theme.json with empty settings for you to complete.
*   Basic: for developers to explore with six templates, two template parts, three block patterns, and two custom block styles alongside some initial theme.json settings.
*   Advanced: for developers to explore with seven templates, five template parts, seven patterns, various block styles, and a more robust theme.json. It’s common to want to remove some of the examples.

**Comparison Chart**

<table><tbody><tr><td><strong>Tool</strong></td><td><strong>Child theme options?</strong></td><td><strong>Template creation?</strong></td><td><strong>Theme.json Controls</strong></td><td><strong>Demo content</strong></td></tr><tr><td>Create Block Theme plugin</td><td>Yes</td><td>Yes</td><td>No</td><td>No</td></tr><tr><td>Theme Generator</td><td>No</td><td>Yes</td><td>Yes</td><td>Yes</td></tr></tbody></table>

## Classic themes

A classic theme is built with PHP templates, functions.php, and more. You can read more about these themes in the [Classic Theme section](https://developer.wordpress.org/themes/classic-themes/).

The [\_s (Underscores)](https://underscores.me/) starter theme is a tool for initializing and creating a classic theme.

## Tools

**WordPress Coding Standards for PHP\_CodeSniffer**

This project is a collection of [PHP\_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) rules (sniffs) that are used to validate code developed for WordPress, but can also be used when developing themes and plugins. They encompass coding style along with established best practices regarding interoperability, translatability, and security in the WordPress ecosystem, according to the official [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/).

[WordPress Coding Standards for PHP\_CodeSniffer](https://github.com/WordPress/WordPress-Coding-Standards)

The WPThemeReview Standards for PHP\_CodeSniffer are a collection of sniffs that aim to automate the code analysis part of the [Theme Review Process](https://make.wordpress.org/themes/handbook/review/) as much as possible using static code analysis.  
The WPThemeReview Standards require the WordPress Coding Standards.

[WPThemeReview Standards for PHP\_CodeSniffer](https://github.com/WPTT/WPThemeReview) 

[**Theme Check Plugin**](https://wordpress.org/plugins/theme-check/)

The theme check plugin is an easy way to test your theme and make sure it’s up to spec with the latest [theme review](https://make.wordpress.org/themes/handbook/review/) standards. With it, you can run all the same automated testing tools on your theme that WordPress.org uses for theme submissions. This allows you to resolve any issues that might come up before trying to submit your theme to the theme repository. 

## Training material

Site Design with Full Site Editing: [Part 1](https://learn.wordpress.org/course/simple-site-design-with-full-site-editing/), [Part 2](https://learn.wordpress.org/course/part-2-personalized-site-design-with-full-site-editing-and-theme-blocks/), [Part 3](https://learn.wordpress.org/course/part-3-advanced-site-design-with-full-site-editing-site-editor-templates-and-template-parts/)

[Anatomy of a Block Theme](https://learn.wordpress.org/tutorial/anatomy-of-a-block-theme/)

[Creating a landing page with a block theme](https://learn.wordpress.org/tutorial/creating-a-landing-page-with-a-block-theme/)

[Building a home page with a block theme](https://learn.wordpress.org/tutorial/building-a-home-page-with-a-block-theme/)

[Using Schema with WordPress theme.json](https://learn.wordpress.org/tutorial/using-schema-with-wordpress-theme-json/)

[Create a Basic Child Theme for Block Themes](https://learn.wordpress.org/lesson-plan/create-a-basic-child-theme-for-block-themes/)

Find more theme lessons on [learn.wordpress.org](https://learn.wordpress.org/?s=theme).