# Theme Security

## Introduction

The WordPress development team takes security seriously. With so much of the web relying on the integrity of the platform, security is a necessity. While the core developers have a dedicated team focused on securing the core platform, as a theme developer you are quite aware that there is potentially much that is outside the core which can be vulnerable. Because WordPress provides so much power and flexibility, plugins and themes are key points of weakness.

### Developing a Security Mindset

When developing your themes, it is important to consider security as you add functionality. Use the following principles as you begin your theme development efforts:

*   **Don’t trust any data.** Don’t trust user input, third-party APIs, or data in your database without verification. Protection of your WordPress themes begins with ensuring the data entering and leaving your theme is as intended. Always make sure to validate on input and sanitize (escape) data before use or on output.
*   **Rely on the WordPress API.** Many core WordPress functions provide the build in the functionality of validating and sanitizing data. Rely on the WordPress provided functions when possible.
*   **Keep your themes up to date.** As technology evolves, so does the potential for new security holes in your themes. Stay vigilant maintaining your code and updating your themes as required.

This chapter provides some background on writing secure themes with [data validation](https://developer.wordpress.org/themes/theme-security/data-validation/) and [sanitization/escaping](https://developer.wordpress.org/themes/theme-security/data-sanitization-escaping/) techniques, [using nonces](https://developer.wordpress.org/themes/theme-security/using-nonces/) to generate secure tokens, and a review of the [common security attacks](https://developer.wordpress.org/themes/theme-security/common-vulnerabilities/), and how you can harden your theme against them.

### Additional Resources

*     A Guide to Writing WordPress Themes – WordPress.org Blog Series
    *   [A Guide to Writing Secure Themes – Part 1: Introduction](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)
    *   [A Guide to Writing Secure Themes – Part 2: Validation](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)
    *   [A Guide to Writing Secure Themes – Part 3: Sanitization](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)
    *   [A Guide to Writing Secure Themes – Part 4: Securing Post Meta](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)
*   [Sucuri Security Blog](https://blog.sucuri.net/)