# Main Stylesheet (style.css)

The style.css is a stylesheet (CSS) file required for every WordPress theme. It controls the presentation (visual design and layout) of the website pages.

## Location

In order for WordPress to recognize the set of theme template files as a valid theme, the style.css file needs to be located in the root directory of your theme, not a subdirectory.

For more detailed explanation on how to include the style.css file in a theme, see the “Stylesheets” section of [Enqueuing Scripts and Styles](https://developer.wordpress.org/themes/basics/including-css-javascript/#stylesheets).

## Basic Structure

WordPress uses the header comment section of a style.css to display information about the theme in the Appearance (Themes) dashboard panel.

### Example

Here is an example of the header part of style.css.

```css
/*
Theme Name: Twenty Twenty
Theme URI: https://wordpress.org/themes/twentytwenty/
Author: the WordPress team
Author URI: https://wordpress.org/
Description: Our default theme for 2020 is designed to take full advantage of the flexibility of the block editor. Organizations and businesses have the ability to create dynamic landing pages with endless layouts using the group and column blocks. The centered content column and fine-tuned typography also makes it perfect for traditional blogs. Complete editor styles give you a good idea of what your content will look like, even before you publish. You can give your site a personal touch by changing the background colors and the accent color in the Customizer. The colors of all elements on your site are automatically calculated based on the colors you pick, ensuring a high, accessible color contrast for your visitors.
Tags: blog, one-column, custom-background, custom-colors, custom-logo, custom-menu, editor-style, featured-images, footer-widgets, full-width-template, rtl-language-support, sticky-post, theme-options, threaded-comments, translation-ready, block-styles, wide-blocks, accessibility-ready
Version: 1.3
Requires at least: 5.0
Tested up to: 5.4
Requires PHP: 7.0
License: GNU General Public License v2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html
Text Domain: twentytwenty
This theme, like WordPress, is licensed under the GPL.
Use it to make something cool, have fun, and share what you've learned with others.
*/
```

WordPress Theme Repository uses the number after “Version” in this file to determine if the theme has a new version available.

### Explanations

Items indicated with (*\**) are required for a theme in the WordPress Theme Repository.

*   **Theme Name** (\*): Name of the theme.
*   **Theme URI**: The URL of a public web page where users can find more information about the theme.
*   **Author** (\*): The name of the individual or organization who developed the theme. Using the Theme Author’s wordpress.org username is recommended.
*   **Author URI**: The URL of the authoring individual or organization.
*   **Description** (\*): A short description of the theme.
*   **Version** (\*): The version of the theme, written in X.X or X.X.X format.
*   **Requires at least (\*)**: The oldest main WordPress version the theme will work with, written in X.X format. Themes are only required to support the three last versions.
*   **Tested up to (\*):** The last main WordPress version the theme has been tested up to, i.e. 5.4. Write only the number, in X.X format.
*   **Requires PHP (\*)**: The oldest PHP version supported, in X.X format, only the number
*   **License** (\*): The license of the theme.
*   **License URI** (\*): The URL of the theme license.
*   **Text Domain** (\*): The string used for textdomain for translation.
*   **Tags**: Words or phrases that allow users to find the theme using the tag filter. A full list of tags is in the [Theme Review Handbook](https://make.wordpress.org/themes/handbook/review/required/theme-tags/).
*   **Domain Path**: Used so that WordPress knows where to find the translation when the theme is disabled. Defaults to `/languages`.

After the required header section, style.css can contain anything a regular CSS file has.

## Style.css for a Child Theme

If your theme is a Child Theme, the **Template** line is required in style.css header.

```css
/*
Theme Name: My Child Theme
Template: twentytwenty
*/
```

For more information on creating a Child Theme, visit the [Child Themes](/themes/advanced-topics/child-themes/) page.