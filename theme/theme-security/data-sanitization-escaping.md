# Data Sanitization/Escaping

## Sanitization: Securing Input

Sanitization is the process of cleaning or filtering your input data. Whether the data is from a user or an API or web service, you use sanitizing when you don’t know what to expect or you don’t want to be strict with [data validation](https://developer.wordpress.org/themes/theme-security/data-validation/).

The easiest way to sanitize data is with built-in WordPress functions.

The `sanitize_*()` series of helper functions provide an effective way to ensure you’re ending up with safe data, and they require minimal effort on your part:

*   [sanitize\_email()](https://developer.wordpress.org/reference/functions/sanitize_email/)
*   [sanitize\_file\_name()](https://developer.wordpress.org/reference/functions/sanitize_file_name/)
*   [sanitize\_html\_class()](https://developer.wordpress.org/reference/functions/sanitize_html_class/)
*   [sanitize\_key()](https://developer.wordpress.org/reference/functions/sanitize_key/)
*   [sanitize\_meta()](https://developer.wordpress.org/reference/functions/sanitize_meta/)
*   [sanitize\_mime\_type()](https://developer.wordpress.org/reference/functions/sanitize_mime_type/)
*   [sanitize\_option()](https://developer.wordpress.org/reference/functions/sanitize_option/)
*   [sanitize\_sql\_orderby()](https://developer.wordpress.org/reference/functions/sanitize_sql_orderby/)
*   [sanitize\_text\_field()](https://developer.wordpress.org/reference/functions/sanitize_text_field/)
*   [sanitize\_title()](https://developer.wordpress.org/reference/functions/sanitize_title/)
*   [sanitize\_title\_for\_query()](https://developer.wordpress.org/reference/functions/sanitize_title_for_query/)
*   [sanitize\_title\_with\_dashes()](https://developer.wordpress.org/reference/functions/sanitize_title_with_dashes/)
*   [sanitize\_user()](https://developer.wordpress.org/reference/functions/sanitize_user/)
*   [esc\_url\_raw()](https://developer.wordpress.org/reference/functions/esc_url_raw/)
*   [wp\_filter\_post\_kses()](https://developer.wordpress.org/reference/functions/wp_filter_post_kses/)
*   [wp\_filter\_nohtml\_kses()](https://developer.wordpress.org/reference/functions/wp_filter_nohtml_kses/)

Tip: **Any time you’re accepting potentially unsafe data, it is important to validate or sanitize it.**

### Example -Simple Input Field

Let’s say we have an input field named title.

<input id="title" type="text" name="title">

You can sanitize the input data with the [sanitize\_text\_field()](https://developer.wordpress.org/reference/functions/sanitize_text_field/) function:

$title = sanitize\_text\_field( $\_POST\['title'\] );
update\_post\_meta( $post->ID, 'title', $title );

Behind the scenes, [sanitize\_text\_field()](https://developer.wordpress.org/reference/functions/sanitize_text_field/) does the following:

*   Checks for invalid UTF-8
*   Converts single less-than characters (<) to entity
*   Strips all tags
*   Removes line breaks, tabs and extra white space
*   Strips octets

Tip: Remember, rely on the WordPress API and its help functions to assist with securing your themes.

## Escaping: Securing Output

Whenever you’re outputting data make sure to properly **escape it**.

**Escaping is the process of securing output by stripping out unwanted data, like malformed HTML or script tags, preventing this data from being seen as code.**

Escaping helps secure your data prior to rendering it for the end user and prevents XSS (Cross-site scripting) attacks.

Note:  
[Cross-site scripting (XSS)](https://en.wikipedia.org/wiki/Cross-site_scripting) is a type of computer security vulnerability typically found in web applications. XSS enables attackers to inject client-side scripts into web pages viewed by other users. A cross-site scripting vulnerability may be used by attackers to bypass access controls such as the same-origin policy.

WordPress has a few helper functions you can use for most common scenarios.

*   [esc\_html()](https://developer.wordpress.org/reference/functions/esc_html/) – Use this function anytime an HTML element encloses a section of data being displayed.

<?php echo esc\_html( $title ); ?>

*   [esc\_url()](https://developer.wordpress.org/reference/functions/esc_url/) – Use this function on all URLs, including those in the `src` and `href` attributes of an HTML element.

<img src="<?php echo esc\_url( $great\_user\_picture\_url ); ?>" />

*   [esc\_js()](https://developer.wordpress.org/reference/functions/esc_js/) – Use this function for inline Javascript.

<a href="#" onclick="<?php echo esc\_js( $custom\_js ); ?>">Click me</a>

*   [esc\_attr()](https://developer.wordpress.org/reference/functions/esc_attr/) – Use this function on everything else that’s printed into an HTML element’s attribute.

<ul class="<?php echo esc\_attr( $stored\_class ); ?>"> </ul>

*   [esc\_textarea()](https://developer.wordpress.org/reference/functions/esc_textarea/) – encodes text for use inside a textarea element.

<textarea><?php echo esc\_textarea( $text ); ?></textarea>

Tip: Output escaping should occur as late as possible.

### Escaping with Localization

Rather than using `echo` to output data, it’s common to use the WordPress localization functions, such as [\_e()](https://developer.wordpress.org/reference/functions/_e/) or [\_\_()](https://developer.wordpress.org/reference/functions/__/).

These functions simply wrap a localization function inside an escaping function:

esc\_html\_e( 'Hello World', 'text\_domain' );
// same as
echo esc\_html( \_\_( 'Hello World', 'text\_domain' ) );

These helper functions combine localization and escaping:

*   [esc\_html\_\_()](https://developer.wordpress.org/reference/functions/esc_html__/)
*   [esc\_html\_e()](https://developer.wordpress.org/reference/functions/esc_html_e/)
*   [esc\_html\_x()](https://developer.wordpress.org/reference/functions/esc_html_x/)
*   [esc\_attr\_\_()](https://developer.wordpress.org/reference/functions/esc_attr__/)
*   [esc\_attr\_e()](https://developer.wordpress.org/reference/functions/esc_attr_e/)
*   [esc\_attr\_x()](https://developer.wordpress.org/reference/functions/esc_attr_x/)

### Custom Escaping

In the case that you need to escape your output in a specific way, the function [wp\_kses()](https://developer.wordpress.org/reference/functions/wp_kses/) (pronounced “kisses”) will come in handy. For example, there are instances when your want HTML elements or attributes to display in your output.

This function makes sure that only the specified HTML elements, attributes, and attribute values will occur in your output, and normalizes HTML entities.

$allowed\_html = \[
    'a'      => \[
        'href'  => \[\],
        'title' => \[\],
    \],
    'br'     => \[\],
    'em'     => \[\],
    'strong' => \[\],
\];
echo wp\_kses( $custom\_content, $allowed\_html );

[wp\_kses\_post()](https://developer.wordpress.org/reference/functions/wp_kses_post/) is a wrapper function for wp\_kses where `$allowed_html` is a set of rules used by post content.

echo wp\_kses\_post( $post\_content );

## Database Escaping

All data in SQL queries must be SQL-escaped before the SQL query is executed to prevent against [SQL injection attacks](https://developer.wordpress.org/themes/theme-security/common-vulnerabilities/). WordPress provides helper classes to assist with escaping SQL queries `$wpdb`.

### Selecting Data

The escaped SQL query ($sql in this example) can then be used with one of the methods:

*   [$](https://developer.wordpress.org/reference/classes/wpdb/get_row/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->get\_row($sql)
*   [$](https://developer.wordpress.org/reference/classes/wpdb/get_var/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->get\_var($sql)
*   [$](https://developer.wordpress.org/reference/classes/wpdb/get_results/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->get\_results($sql)
*   [$](https://developer.wordpress.org/reference/classes/wpdb/get_col/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->get\_col($sql)
*   [$](https://developer.wordpress.org/reference/classes/wpdb/query/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->query($sql)

### Inserting and Updating Data

*   [$](https://developer.wordpress.org/reference/classes/wpdb/update/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->update()
*   [$](https://developer.wordpress.org/reference/classes/wpdb/insert/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->insert()

### Like Statements

*   [$](https://developer.wordpress.org/reference/classes/wpdb/prepare/)[wpdb](https://developer.wordpress.org/reference/classes/wpdb/)\->prepare