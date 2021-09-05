# Common Vulnerabilities

Security is an ever-changing landscape, and vulnerabilities evolve over time. The following is a discussion of common vulnerabilities you should protect against, and the techniques for protecting your theme from exploitation.

## Types of Vulnerabilities

### SQL Injection

**What it is:**  
SQL injection happens when values being inputted are not properly sanitized allowing for any SQL commands in the inputted data to potentially be executed. To prevent this, the WordPress API is extensive, offering functions like `add_post_meta();` instead of you needing to adding the post meta manually via SQL (`INSERT INTO wp_postmeta…`).

![exploits_of_a_mom](https://make.wordpress.org/docs/files/2013/03/exploits_of_a_mom.png)

xkcd [Exploits of a Mom](https://xkcd.com/327/)

The first rule for hardening your theme against SQL injection is: When there’s a WordPress function, use it.

But sometimes you need to do complex queries, that have not been accounted for in the API. If this is the case, always use the [`$wpdb` functions](https://developer.wordpress.org/reference/classes/wpdb/). These were built specifically to protect your database.

All data in SQL queries must be SQL-escaped before the SQL query is executed to prevent against SQL injection attacks. The best function to use for SQL-escaping is `$wpdb->prepare()` which supports both a [sprintf()](http://secure.php.net/sprintf)\-like and [vsprintf()](http://secure.php.net/vsprintf)\-like syntax.

<br />
$wpdb->get\_var( $wpdb->prepare(<br />
  &quot;SELECT something FROM table WHERE foo = %s and status = %d&quot;,<br />
  $name, // an unescaped string (function will do the sanitization for you)<br />
  $status // an untrusted integer (function will do the sanitization for you)<br />
) );<br />

### Cross Site Scripting (XSS)

Cross Site Scripting (XSS) happens when a nefarious party injects JavaScript into a web page.

Avoid XSS vulnerabilities by escaping output, stripping out unwanted data. As a theme’s primary responsibility is outputting content, a theme should [escape dynamic content](https://developer.wordpress.org/themes/theme-security/data-sanitization-escaping/) with the proper function depending on the type of the content.

An example of one of the escaping functions is escaping URL from a user profile.

<br />
&lt;img src=&quot;&lt;?php echo esc\_url( $great\_user\_picture\_url ); ?>&quot; /><br />

Content that has HTML entities within can be sanitized to allow only specified HTML elements.

<br />
$allowed\_html = array(<br />
    'a' => array(<br />
        'href' => array(),<br />
        'title' => array()<br />
    ),<br />
    'br' => array(),<br />
    'em' => array(),<br />
    'strong' => array(),<br />
);</p>
<p>echo wp\_kses( $custom\_content, $allowed\_html );<br />

### Cross-site Request Forgery (CSRF)

Cross-site request forgery or CSRF (pronounced sea-surf) is when a nefarious party tricks a user into performing an unwanted action within a web application they are authenticated in. For example, a phishing email might contain a link to a page that would delete a user’s account in the WordPress admin.

If your theme includes any HTML or HTTP-based form submissions, use a [nonce](https://developer.wordpress.org/themes/theme-security/using-nonces/) to guarantee a user intends to perform an action.

</p>
<p>&lt;form method=&quot;post&quot;><br />
   &lt;!-- some inputs here ... --><br />
   &lt;?php wp\_nonce\_field( 'name\_of\_my\_action', 'name\_of\_nonce\_field' ); ?><br />
&lt;/form></p>
<p>

### Staying Current

It is important to stay current on potential security holes. The following resources provide a good starting point:

*   [WordPress Security Whitepaper](https://wordpress.org/about/security/)
*   [WordPress Security Release](https://wordpress.org/news/category/security/)
*   [Open Web Application Security Project (OWASP) Top 10](https://www.owasp.org/index.php/OWASP_Top_Ten_Cheat_Sheet)