# What is a Theme?

A WordPress theme changes the design of your website, often including its layout. Changing your theme changes how your site looks on the front-end, i.e. what a visitor sees when they browse to your site on the web. There are thousands of free WordPress themes in the [WordPress.org Theme Directory](https://wordpress.org/themes/), though many WordPress sites use custom themes.

## What can themes do?

Themes take the content and data stored by WordPress and display it in the browser. When you create a WordPress theme, you decide how that content looks and is displayed. There are many options available to you when building your theme. For example:

*   Your theme can have different layouts, such as static or responsive, using one column or two.

*   Your theme can display content anywhere you want it to be displayed.

*   Your theme can specify which devices or actions make your content visible.

*   Your theme can customize its typography and design elements using CSS or [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/).

*   Other design elements like images and videos can be included anywhere in your theme.

WordPress themes are incredibly powerful. But, as with every web design project, a theme is more than color and layout. Good themes improve engagement with your website’s content *in addition* to being beautiful.

## What are themes made of?

At their most basic level, WordPress themes are collections of different files that work together to create what you see, as well as how your site behaves.

### Required files

There are only **two files absolutely required in a WordPress** theme:

1.  `index.php` (classic themes) or `index.html` (block themes) – the main template file

3.  `style.css` – the main style file

Though not required, you may see additional files in a theme’s folder including:

*   Classic themes are built with PHP files – including [template files](https://developer.wordpress.org/themes/basics/template-files/ "Template Files Page")

*   Block themes are built with blocks and HTML files

*   [Localization files](https://developer.wordpress.org/theme/functionality/localization/ "Link to the localization section of the theme developer handbook")

*   CSS files

*   Graphics

*   JavaScript

*   Text files – usually license info*,* `readme.txt` instructions, and a changelog file

## What is the difference between a theme and a plugin?

It is common to find cross-over between features found in themes and plugins. However, best practices are:

*   a theme controls the *presentation* of content; whereas

*   a plugin is used to control the behavior and features of your WordPress site.

**Any theme you create should not add critical functionality.** Doing so means that when a user changes their theme, they lose access to that functionality. For example, say you build a theme with a portfolio feature. Users who build their portfolio with your feature will lose it when they change themes.

By moving critical features to plugins, you make it possible for the design of your website to change, while the functionality remains the same.

Note: Remember, some users switch themes often. It is best practice to make sure any functionality your site requires, even if the design changes, is in a separate plugin.

## Themes on WordPress.org

One of the safest places to download WordPress themes is in the [WordPress.org Theme Directory](https://wordpress.org/themes/ "WordPress Theme Directory"). All themes are closely reviewed, and must meet rigorous [theme review guidelines](https://developer.wordpress.org/theme/release/theme-review-guidelines/ "WordPress Theme Review Guidelines") to ensure quality and security.

## Getting Started

Now you know what a theme is it’s time to get started. If you haven’t already done so yet, you should [set up your local development environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/). You can then [check out some examples of WordPress themes](https://developer.wordpress.org/themes/getting-started/theme-development-examples/) or, continue to the next section, [Theme Basics](https://developer.wordpress.org/themes/basics/).