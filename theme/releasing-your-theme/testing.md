# Testing

If you’ve followed this handbook, you’ll already have a good grasp on the testing required before submitting your theme to the WordPress.org theme directory. If you haven’t, this page will give you a quick refresher.

Testing is incredibly important before releasing a theme. You may have built the most beautiful WordPress theme, but if it breaks when someone tries to comment or insert an image, your theme isn’t ready for real world usage.

Before testing your theme, make sure you’ve setup a development environment. There are a number of ways to setup your environment, many of which are documented on the [Setting up a Development Environment](https://developer.wordpress.org/themes/getting-started/setting-up-a-development-environment/) page.

## Theme Unit Test

After you’ve setup your development environment, you’ll need test content to test your theme with. While you can create your own test content, the theme review team has created the [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test), which includes many different types of content. This will help ensure that your theme works in circumstances you may not have anticipated.

The Theme Unit Test is a WordPress export file that can be imported into any WordPress installation by using the WordPress Importer. You should import it into your local development environment.

## WordPress Settings

Making tweaks and changes to your WordPress installation is another good way to ensure that you’ve built your theme to handle numerous scenarios. Use the following settings to test your theme.

**General**  
Set the Site Title to something long and set the Tagline to something even longer. These settings will test how your theme handles edge cases for site titles and taglines.

**Reading**  
Set “Blog pages show at most” to 5. This setting will ensure that index/archive pagination is triggered.

**Discussion**  
Enable “Threaded Comments” at least 3 levels deep. This setting will facilitate testing of your theme’s comment list styling.

Enable “Break comments into pages” and set 5 comments per page to test the pagination and styling of comments.

**Media**  
Remove the values for the large size of media to test the theme’s `$content_width` setting.

**Permalinks**  
Change the permalink setting a few times to ensure your theme can handle various URL formats.

For more setup instructions, take a look at the [Theme Unit Test](https://codex.wordpress.org/Theme_Unit_Test#Setup) page in the WordPress Codex.

## WordPress Beta Tester

WordPress releases happen three times a year. It’s a good idea to test your theme against the next version of WordPress so you can anticipate issues when the next version is released. This can be done easily with the [WordPress Beta Tester](https://wordpress.org/plugins/wordpress-beta-tester/) plugin. The plugin makes it easy to download either the latest nightly version of WordPress or the latest branch version (for minor bugfix releases). This is especially useful when anticipating a new major release or developing for an upcoming feature.

## Testing and debugging tools

### Theme Check

Each theme goes through an automated check before a reviewer even sees it. If there are any immediate problems with the theme, identified by the automated check, the theme will be rejected with notes on how to resolve the issues. The [Theme Check](https://wordpress.org/plugins/theme-check/) plugin adds a dashboard link under Appearance so you can run the exact same checks that WordPress.org does right from your administration panel. Doing this prior to uploading your theme lets you know what needs to be addressed prior to submission. Running the check will give you a list of any warnings your theme has generated and what items are required for the theme to be accepted in the WordPress.org theme directory, as well as any recommended items that may be missing from your theme.

### Developer

The [Developer](https://wordpress.org/plugins/developer/) plugin is really just a tool to automatically download and install some of the plugins you’ll want when developing your theme. Some of the ones discussed in this handbook will already be installed and active. Others you can install as soon as you activate the plugin.

### Debug Bar

[Debug Bar](https://wordpress.org/plugins/debug-bar/) pushes all debug messages to a separate page where they are listed in an easy-to-read layout and organized by type of message. There are also a number of [other plugins](https://wordpress.org/plugins/search.php?q=debug+bar) that add on to Debug Bar, extending its features or adding more information.

### Log Deprecated Notices

[Log Deprecated Notices](https://wordpress.org/plugins/log-deprecated-notices/) displays a list of the deprecated function notices in your theme and where the code can be found. This should be run, at minimum, after every major release of WordPress, so you can resolve and remove any deprecated code and functions from your theme.

### Browser testing

When submitting your theme to WordPress.org, it’s expected that it works well in modern browsers and at any resolution. You should test your theme against a number of popular browsers before submitting, both mobile and desktop. Many browsers have built-in features making it easy to test, for example the [Chrome Developer Tools](https://developer.chrome.com/devtools), [Firefox Developer Tools](https://developer.mozilla.org/en-US/docs/Tools), and the [Microsoft Edge tools](http://dev.modern.ie). Note that [Internet Explorer is no longer supported by WordPress](https://make.wordpress.org/core/2021/04/22/ie-11-support-phase-out-plan/) since 5.8 release.

### Validation

Likewise, your theme should use valid HTML5 and CSS code. There are a variety of tools that will test your site for valid code, include [this HTML5 validator](http://html5.validator.nu/) and [this CSS validator](http://jigsaw.w3.org/css-validator/).