# Writing Documentation

Documentation is important for themes as it provides a way for users to understand what a theme does and does not support. Likewise, documenting the code of your theme will make it easier for other theme developers to customize your theme, likely with a [child theme](https://developer.wordpress.org/themes/advanced-topics/child-themes/).

Here’s a list of **requirements** and **recommendations** for your theme’s documentation.

*   Themes are **required** to provide end-user documentation of any design limitations or extraordinary installation/setup instructions.
*   Themes are **required** to include a [readme.txt file](https://wordpress.org/plugins/about/readme.txt), using the plugin directory’s readme.txt markdown format. New themes need to follow this rule as of October 25th, 2018. Old themes have a 6 months grace time from this date. Since WordPress 5.8 theme [readme files are not parsed for requirements](https://core.trac.wordpress.org/ticket/48520). This means that headers `Requires PHP` and `Requires at least` are going to be parsed from theme’s `style.css` file.