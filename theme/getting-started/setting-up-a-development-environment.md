# Setting up a Development Environment

## Why set up a development environment?

When developing themes, it is best to do it in an environment identical to the production server which will eventually host your WordPress installation.  Your development environment can either be local or remote.  Configuring a local environment to work on your WordPress theme is beneficial for several reasons:

*   You can build your theme locally without relying on a remote server. This speeds up your development process and allows you to see changes instantly in your browser.
*   You do not need an Internet connection to build your theme.
*   You can test your theme from a variety of perspectives. This is important, especially if you plan on releasing your theme to a larger audience and want to ensure maximum compatibility.

## Your WordPress local development environment

For developing WordPress themes, you need to set up a development environment suited to WordPress.  To get started, you will need a local server stack and a text editor. There are a number of options, for example MAMP, XAMPP, Varying Vagrant Vagrants (VVV) or Docker. For more information see [Installing a local server.](https://make.wordpress.org/core/handbook/tutorials/installing-a-local-server/)

**Text Editor**

In addition to a local server environment, you also need a text editor to write your code. Your choice of text editor is personal, but remember that a good text editor can speed up your development process. Your text editor can be everything from a basic tool for writing code to a fully integrated development environment (IDE) with tools for debugging and testing. It’s worth doing research, and some even include support for WordPress development. Popular choices are Atom, Sublime Text, VSCode and PhpStorm.

## Supporting older versions of WordPress

It’s standard practice for WordPress themes to support *at least two versions back* to ensure a minimum of backward compatibility. For example, if the current version of WordPress is at 5.8, then you should also make sure that your theme works well in versions 5.7 and 5.6 as well.

You can refer to the [WordPress Releases](https://wordpress.org/download/releases/) page to access older versions of WordPress. Then you can download and install older WordPress versions, creating multiple development sites, each running different WordPress versions for testing.

## WP\_DEBUG

Configuring debugging is an essential part of WordPress theme development. WordPress provides a number of constants to support your debugging efforts. These includes:

**WP\_DEBUG**

The [WP\_DEBUG](https://codex.wordpress.org/WP_DEBUG "WP_DEBUG") PHP constant is used to trigger the built-in “debug” mode on your WordPress installation. This allows you to view errors in your theme. To enable it:

1\. Open your WordPress installation’s *wp-config.php* file

2\. Change:

```php
define( 'WP_DEBUG', false );
```

to

```php
define( 'WP_DISABLE_FATAL_ERROR_HANDLER', true ); // 5.2 and later
define( 'WP_DEBUG', true );
```

Note: While normally set to ‘false’ in the *wp-config.php* file, development copies of WordPress—alpha and beta versions of the upcoming release—WP\_DEBUG is already set to ‘true’ by default.

**WP\_DEBUG\_DISPLAY and WP\_DEBUG\_LOG**

[WP\_DEBUG\_LOG](https://codex.wordpress.org/Debugging_in_WordPress#WP_DEBUG_LOG) and [WP\_DEBUG\_DISPLAY](https://codex.wordpress.org/Debugging_in_WordPress#WP_DEBUG_DISPLAY) are additional PHP constants which extend WP\_DEBUG.

WP\_DEBUG\_LOG is used in conjunction with WP\_DEBUG to log all error messages to a debug.log within your WordPress /wp-content/ directory. To enable this functionality set WP\_DEBUG\_LOG to true within your wp-config.php file.

```php
define( 'WP_DEBUG_LOG', true );
```

WP\_DEBUG\_DISPLAY is used to control whether debug messages display within the HTML of your theme pages. To display error messages on the screen as they occur, configure this setting to ‘true’ within your *wp-config.php* file.

```php
define( 'WP_DEBUG_DISPLAY', true );
```

With the WP\_DEBUG and WP\_DEBUG\_DISPLAY enabled, error messages will display at the top of your site pages.

[![admin-sample-debug](https://developer.wordpress.org/files/2014/07/admin-sample-debug.png)](https://developer.wordpress.org/files/2014/07/admin-sample-debug.png)

Note: Errors will display in the frontend and admin areas of your site. These debug tools are meant for local testing and staging installs, not for live sites.

## Other WordPress Development Tools

In addition to WP\_DEBUG, the following plugins and unit test data sets are an important part of your development toolset and help you develop better WordPress themes.

#### Test Data

**WordPress.org Theme Test Data**

[WordPress.org Theme Test Data](https://codex.wordpress.org/Theme_Unit_Test) is an XML file containing dummy test data that you can upload to test how themes perform with different types and layouts of content.

**WordPress.com Theme Unit Test Data**

[WordPress.com Theme Unit Test Data](http://themetest.wordpress.com/) is dummy test data that you can upload to a WordPress installation to test your theme, including WordPress.com-specific features.

#### Plugins

**Debug Bar** **(WordPress plugin)**

[Debug Bar](https://wordpress.org/plugins/debug-bar/) adds an admin bar to your WordPress admin providing a central location for debugging.

**Query Monitor** **(WordPress plugin)**

[Query Monitor](https://wordpress.org/plugins/query-monitor/) allows debugging of database queries, API request and AJAX called used to generate theme pages and theme functionality.

**Log Deprecated Notices** **(WordPress plugin)**

[Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/) logs incorrect function usage and the use of deprecated files and functions in your WordPress theme.

**Monster Widgets** **(WordPress plugin)**

[Monster Widget](https://wordpress.org/plugins/monster-widget/) consolidates the core WordPress widgets into a single widget allowing you to test widgets styling and functionality in your theme.

**Theme-Check (WordPress plugin)**

[Theme-Check](https://wordpress.org/plugins/theme-check/ "Theme-Check: A simple and easy way to test your theme for all the latest WordPress standards and practices.") tests your theme for compliance with the latest WordPress standards and practices.

## WordPress Theme Review Guidelines

In addition to the above development tools, it’s a good idea to stay up to date on the WordPress.org Themes Team’s [guidelines for theme submission](https://make.wordpress.org/themes/handbook/review/required/) and guidance on meeting [WordPress Coding Standards](https://make.wordpress.org/core/handbook/best-practices/coding-standards/). These guidelines are the “gold standard” for quality theme development and are useful, even if you don’t plan on releasing a theme on WordPress.org.
