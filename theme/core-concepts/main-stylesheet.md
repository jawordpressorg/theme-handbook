# Main Stylesheet (style.css)

As described in [Theme Structure](https://developer.wordpress.org/themes/core-concepts/theme-structure/), WordPress requires that all themes include a `style.css` file. Its most important function is to “register” the theme with WordPress through configuration data at the top of the file. Many themes also use it to serve CSS to the front-end (and even the editor).

In this document, you will learn how to configure your theme data via the `style.css` file header.

## File Header

The `style.css` file header is used to configure data about the theme. WordPress uses this information to determine how some features work and displays some of this data under the **Appearance > Themes** screen for users.

Here is a look at what the theme details overlay looks like for the default Twenty Twenty-Three theme:

[![WordPress themes screen with the Twenty Twenty-Three modal overlay over the screen. It shows the theme screenshot, description, and metadata.](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?resize=2048%2C1002&ssl=1)](https://i0.wp.com/developer.wordpress.org/files/2023/11/tt3-theme-details.jpg?ssl=1)

Most of that information is pulled directly from the `style.css` file header. It is one of the most vital parts of creating a WordPress theme.

When determining which themes are available to activate, WordPress searches through each folder under `/wp-content/themes`, looking for a `style.css` file. If one is found, it pulls the first 8kb of data from the file and determines if there is a file header with standard fields defined.

In themes, this is merely a CSS comment block with some standard keys and values defined.

Suppose you were creating a theme with the folder name of `fabled-sunset`. WordPress would look for your theme’s `style.css` in the following location:

*   `wp-content/`
    *   `themes/`
        *   `fabled-sunset/`
            *   `style.css`

For WordPress to recognize your theme, you would at least need the `Theme Name` field defined at the top of `style.css` like so:

```css
/**
 * Theme Name: Fabled Sunset
 */
```

This is the minimum required header field for a valid theme. Of course, you’ll want to add much more information about your theme.

### Header fields

There are many supported fields, and you will likely use most of them in your themes. Here is a quick look at a theme’s `style.css` file header with each of the fields configured:

```css
/**
 * Theme Name:        Fabled Sunset
 * Theme URI:         https://example.com/fabled-sunset
 * Description:       Custom theme description...
 * Version:           1.0.0
 * Author:            Your Name
 * Author URI:        https://example.com
 * Tags:              block-patterns, full-site-editing
 * Text Domain:       fabled-sunset
 * Domain Path:       /assets/lang
 * Tested up to:      6.4
 * Requires at least: 6.2
 * Requires PHP:      7.4
 * License:           GNU General Public License v2.0 or later
 * License URI:       https://www.gnu.org/licenses/gpl-2.0.html
 */
```

The following list outlines what each of these fields does.

While the `Theme Name` is the only field required to work with WordPress, you must also include some other fields when submitting a theme to the WordPress theme directory. These fields are marked with **\*** below.

*   **Theme Name\*:** A unique name for your theme.
*   **Theme URI:** The URL of a public web page where users can find more information about the theme.
*   **Description\*:** A description of the theme, which will be displayed when viewing a theme’s details in the WordPress admin and other places. It is also used for themes submitted to the WordPress theme directory.
*   **Version\*:** The version of the theme, written in `X.X` or `X.X.X` format.
*   **Author\*:**  Your name or the name of the organization who developed the theme. For themes submitted to the theme directory, it is recommended to use the WordPress.org username.
*   **Author URI:** The URL of the individual or organization who created the theme.
*   **Tags:** A comma-separated list of features the theme supports. The Theme Review Handbook has a [list of valid tags](https://make.wordpress.org/themes/handbook/review/required/theme-tags/) for submission to the theme directory, but third-party sites may use a different system.
*   **Text Domain\*:** The string used for the textdomain for translations.
*   **Domain Path:** A relative path to where theme translations are stored. WordPress uses this field when the theme is disabled to detect translations. Defaults to `/languages`.
*   **Tested up to\*:** The last WordPress version the theme has been tested up to, written in `X.X` format (e.g., `6.`4, `6.2.1`, etc.).
*   **Requires at least\*:** The oldest WordPress version the theme will work with, written in `X.X` format (e.g., `6.3`, `6.2.1`, etc.).
*   **Requires PHP\*:** The oldest PHP version the theme will work with, written in `X.X` format (e.g., `8.0`, `7.4`, etc.).
*   **License\*:** The license for the theme.
*   **License URI\*:** The URL of the theme’s license.

### Child theme header fields

When building a child theme, there is one additional supported field: **Template**. This is used to designate the parent theme’s folder.

If the fictional “Fabled Sunset” theme listed above was the parent of your child theme named “Grand Sunrise,” your `style.css` header fields would look similar to this:

```css
/**
 * Theme Name: Grand Sunrise
 * Template:   fabled-sunset
 * ...other header fields
 */
```

The `Template` field must match the parent theme’s folder name exactly (relative to the `wp-content/themes` directory) for this to work. Otherwise, WordPress will not be able to appropriately match them.

You can [learn more about child themes](https://developer.wordpress.org/themes/advanced-topics/child-themes/) in the Advanced Topics chapter.

### Custom header fields

Some third-party marketplaces or systems may also make use of custom header fields. These are not officially supported by WordPress, but they are definitely allowed and should not negatively impact how the theme works within WordPress.

## Custom CSS

The `style.css` file is not merely a configuration file. You can also use it to write custom CSS code to alter the design of your theme, assuming the file is properly loaded.

With block themes, most or all of the design is ideally handled through the `theme.json` file, which you will learn about in the [Global Settings and Styles](https://developer.wordpress.org/themes/core-concepts/global-settings-and-styles/) documentation.

But there are times when you will want or need to add custom CSS. You can learn more about this in the [Including Assets](https://developer.wordpress.org/themes/core-concepts/including-assets/) documentation.