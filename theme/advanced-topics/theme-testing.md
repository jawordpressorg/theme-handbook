# Theme Testing

The [Theme Unit Test data](https://github.com/WPTRT/theme-unit-test/blob/master/themeunittestdata.wordpress.xml) is a WordPress import file will fill a WordPress site with enough stub data (posts, media, users) to test a theme.

The Theme Unit Tests are manual tests to walk through to test theme functionality and how the theme responds to the edge-cases of content and settings.

### Theme Unit Test Overview

1.  Fix PHP and WordPress errors. Add the following debug setting to your `wp-config.php` file to see deprecated function calls and other WordPress-related errors:   
    `define('WP_DEBUG', true);`  
    See [Deprecated Functions Hook](https://codex.wordpress.org/WordPress_Deprecated_Functions_Hook) for more information.
2.  Check template files against [Template File Checklist](https://developer.wordpress.org/themes/template-files-section/) (see above).
3.  Do a run-through using the [Theme Unit Test](https://make.wordpress.org/themes/handbook/review/theme-unit-test/).
4.  Validate HTML and CSS. See [Validating a Website](https://developer.wordpress.org/themes/advanced-topics/validating-your-theme/).
5.  Check for JavaScript errors.
6.  Test in all your target browsers. For example Safari, Chrome, Opera, Firefox and Microsoft Edge.
7.  Clean up any extraneous comments, debug settings or TODO items.
8.  See [Theme Review](https://make.wordpress.org/themes/handbook/review/) if you are publicly releasing the Theme by submitting it to the Themes Directory.