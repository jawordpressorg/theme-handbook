# Theme Development Examples

One of the best ways to understand theme coding standards is to find examples of other themes that have been written with these standards in mind.

## Default “Twenty” themes

Packaged in every version of WordPress since version 3.0 (and named after the year they were released in), the default themes are some of the best to study how themes are built. This is because they are designed with broad use in mind and fully adhere to WordPress coding standards. You can download and study their theme files, and keep them around as examples to reference while learning how to develop your own themes:

*   [Twenty Twenty-One](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentytwentyone)
*   [Twenty Twenty](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentytwenty)
*   [Twenty Nineteen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentynineteen)
*   [Twenty Seventeen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyseventeen)
*   [Twenty Sixteen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentysixteen) [(only packaged in WordPress 4.8)](https://core.trac.wordpress.org/ticket/36497)
*   [Twenty Fifteen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyfifteen)
*   [Twenty Fourteen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyfourteen)
*   [Twenty Thirteen](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentythirteen)
*   [Twenty Twelve](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentytwelve)
*   [Twenty Eleven](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyeleven)
*   [Twenty Ten](https://core.trac.wordpress.org/browser/trunk/src/wp-content/themes/twentyten)

## The Underscores theme

Unlike the default “Twenties” themes, the **\_s** (or Underscores) theme is aimed at developers rather than end-users. It is intended to be a *starter theme* which you can use as a base to speed your development. It has a number of features:

*   Well-commented HTML5 templates, including error templates.
*   A sample custom header implementation in `inc/custom-header.php`.
*   Custom template tags in `inc/template-tags` to keep templates organized and prevent code duplication.
*   A number of scripts to improve keyboard navigation—found in `js/keyboard-image-navigation.js`—as well as small screen navigation in `js/navigation.js`.
*   Five sample CSS layouts in `/layouts` as well as starter CSS on which to build your design.
*   GPL-licensed code.

The features above make Underscores a great theme for a developer wanting to create their own theme. And even if you remove the extras, the base that’s left is a still an excellent example of a well-coded theme, developed with standards and best-practices in mind.

A more detailed overview is available on [Underscores’ website](http://underscores.me/).

[Code for Underscores may be found at github](https://github.com/Automattic/_s/).

## Other Sources

Additionally, all themes published in the [theme directory](https://wordpress.org/themes/) are reviewed for standards prior to being published. [Reviewing themes](https://make.wordpress.org/themes/) in the directory is a great way to better understand how theme development works and is a good way to get inspiration for your own theme.