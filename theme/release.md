# Releasing Your Theme

This section covers the requirements and submission process for releasing your theme into the [WordPress Theme Directory](https://wordpress.org/themes/). If you’ve followed the instructions in this handbook, your theme is almost ready for release into the directory.

The first requirement to releasing your theme is to make sure you have – at minimum – the [required theme files](https://developer.wordpress.org/themes/release/required-theme-files/) before submitting your theme for review.

Once you’ve confirmed the required theme files, thorough [testing](https://developer.wordpress.org/themes/release/testing/) of the theme – including content – must be completed. Following the [theme review guidelines](https://developer.wordpress.org/themes/release/theme-review-guidelines/) will help ensure acceptance of your theme.

After completing everything above, having the proper [documentation](https://developer.wordpress.org/themes/release/writing-documentation/) is the final step before [submitting your theme for approval](https://developer.wordpress.org/themes/release/submitting-your-theme-to-wordpress-org/). After submitting your theme for review, the theme reviewer may request other changes to your theme.

## Important Notices

As we have a large number of tickets in the review queue, reviewers are allowed to close tickets as “not-approved” for themes with more than 3 distinct required issues. If you don’t wish to wait extra months for the next review, take a time to fully understand [Theme Review Guidelines](//developer.wordpress.org/themes/release/theme-review-guidelines/) and strictly follow it.

Tip:  
[“How to do a review (Draft)”](//make.wordpress.org/themes/handbook/review/how-to-do-a-review-draft/) is the another practical guide even for the theme authors to know the detail about review process.

## First Three Checks

Below three checks are very basic ones that many theme authors are missing at the first time.

### 1\. Did you understand the rules of WordPress Theme in repository?

*   Themes must be compatible with the GNU General Public License v2, or any later version.
*   Plugin territory and non-design related functionality are not allowed. Adding shortcodes and custom post types are not allowed in themes.
*   and [more](//developer.wordpress.org/themes/release/theme-review-guidelines/).

### 2\. Did you run Theme Sniffer plugin?

The Theme Sniffer plugin is the test tool using [WordPress-Theme](//github.com/WPTRT/WordPress-Coding-Standards) standard forked from WordPress Coding Standards. For more details, refer to [this document](//github.com/WPTRT/theme-sniffer).

### 3\. Did you run Theme Check plugin?

The Theme Check plugin is an easy way to test your theme and make sure it’s up to spec with the latest theme review standards. For more details, refer to [this document](//make.wordpress.org/themes/handbook/review/required/theme-check-plugin/).