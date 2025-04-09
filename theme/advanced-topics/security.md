# Security

When releasing any code out into the world, whether it will only exist on your own site or hundreds of thousands of sites, it’s important to strive to make it as secure as possible. Responsible coding means being vigilant about all the ways your theme can be exploited.

Your primary source for learning about security in the [Security chapter](https://developer.wordpress.org/apis/security/) in the Common APIs Handbook. This article should be considered a supplement to what you will learn there and is not an all-encompassing guide on security itself. 

Below, you will find a list of common vulnerabilities to consider, but please use the Resources section for a more comprehensive overview of how to secure your themes.

## Common vulnerabilities

Security is an ever-changing landscape, and vulnerabilities evolve over time. The following is an overview of common vulnerabilities you should protect against and the techniques for protecting your theme from exploitation.

### Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) happens when a nefarious party injects JavaScript into a web page.

To avoid XSS vulnerabilities, any output should be escaped. Since it’s the theme’s primary responsibility to output content, you should always [escape dynamic content](https://developer.wordpress.org/apis/security/sanitizing/) with the proper function based on the data type.

This example shows how to escape an image URL to avoid XSS vulnerabilities:

```php
<img src="<?php echo esc_url( $great_user_picture_url ); ?>" />
```

Content that has HTML entities within can be sanitized to allow only specified HTML elements:

```php
$allowed_html = array(
	'a' => array(
		'href' => array()
	),
	'br'     => array(),
	'em'     => array(),
	'strong' => array()
);

echo wp_kses( $custom_content, $allowed_html );
```

### SQL Injection

SQL Injection happens when values being input are not properly sanitized, allowing for any SQL commands in the data to potentially be executed. To prevent this, the WordPress API is extensive. For example, it offers functions like [`add_post_meta()`](https://developer.wordpress.org/reference/functions/add_post_meta/) so that you don’t need to manually insert metadata via SQL.

The first rule for hardening your theme against SQL Injection is: **when there’s a WordPress function, use it.**

While it is rare to do so in themes, sometimes you need to do complex queries that have not been accounted for in the API. If this is the case, always use the [`$wpdb` functions](https://developer.wordpress.org/reference/classes/wpdb/). These were built specifically to protect your database.

All data in SQL queries must be SQL-escaped before the SQL query is executed to prevent SQL injection attacks. The best function to use for SQL-escaping is `$wpdb->prepare()` which supports both a [`sprintf()`](http://secure.php.net/sprintf)\-like and [`vsprintf()`](http://secure.php.net/vsprintf)\-like syntax:

```php
$wpdb->get_var( $wpdb->prepare(
	"SELECT something FROM table WHERE foo = %s and status = %d",
	$name, // an unescaped string (function will do the sanitization for you)
	$status // an untrusted integer (function will do the sanitization for you)
) );
```

### Cross-Site Request Forgery (CSRF)

Cross-site request forgery or CSRF (pronounced *sea-surf*) is when a nefarious party tricks a user into performing an unwanted action within a web application they are authenticated in. For example, a phishing email might contain a link to a page that would delete a user’s account in the WordPress admin.

This is more common in plugins than themes. But if your theme includes any HTML or HTTP-based form submissions, use a [nonce](https://developer.wordpress.org/apis/security/nonces/) to guarantee a user intends to perform an action:

```php
<form method="post">
	<!-- some inputs here ... -->
	<?php wp_nonce_field( 'name_of_my_action', 'name_of_nonce_field' ); ?>
</form>
```

## Resources

Use the resources listed below to dive more deeply into securing your themes, plugins, and anything else you build on top of WordPress:

*   [Common APIs Handbook: Security](https://developer.wordpress.org/apis/security/)
    *   [Escaping Data](https://developer.wordpress.org/apis/security/escaping/)
    *   [Sanitizing Data](https://developer.wordpress.org/apis/security/sanitizing/)
    *   [Validating Data](https://developer.wordpress.org/apis/security/data-validation/)
    *   [Nonces](https://developer.wordpress.org/apis/security/nonces/)
*   Make Themes: A Guide To Writing Secure Themes:
    *   [Part 1: Introduction](https://make.wordpress.org/themes/2015/05/19/a-guide-to-writing-secure-themes-part-1-introduction/)
    *   [Part 2: Validation](https://make.wordpress.org/themes/2015/05/26/a-guide-to-writing-secure-themes-part-2-validation/)
    *   [Part 3: Sanitization](https://make.wordpress.org/themes/2015/06/02/a-guide-to-writing-secure-themes-part-3-sanitization/)
    *   [Part 4: Securing Post Meta](https://make.wordpress.org/themes/2015/06/09/a-guide-to-writing-secure-themes-part-4-securing-post-meta/)

### Staying current

It is important to stay current on potential security holes. The following resources provide a good starting point:

*   [WordPress Security Whitepaper](https://wordpress.org/about/security/)
*   [WordPress Security Release](https://wordpress.org/news/category/security/)
*   [Open Web Application Security Project (OWASP) Top 10](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet)