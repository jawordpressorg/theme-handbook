# Internationalization

Text inside Template or Template parts that are HTML files can not be made translatable.  
  
A pattern block can be used to insert translatable content inside a block template. Since those files are PHP-based, there is a mechanism to mark strings for translation or to supply dynamic URLs.

Example block pattern:

```
<?php
register_block_pattern(
    'myfirsttheme/wordpress-credit',
    array(
        'title'      => __( 'WordPress credit', 'myfirsttheme' ),
        'content'    => '
                        <!-- wp:paragraph -->
                        <p>' .
                        sprintf(
                            /* Translators: WordPress link. */
                            esc_html__( 'Proudly Powered by %s', 'myfirsttheme' ),
                            '<a href="' . esc_url( __( 'https://wordpress.org', 'myfirsttheme' ) ) . '" rel="nofollow">WordPress</a>'
                        ) . '</p>
                        <!-- /wp:paragraph -->',
        'inserter'   => false
    )
);
```

You can hide the pattern from the block inserter using the argument `'inserter' => false`.

Add the pattern in a template or template part using the pattern block:

```
<!-- wp:group -->
<div class="wp-block-group">
    <!-- wp:pattern {"slug":"myfirsttheme/wordpress-credit"} /-->
</div>
<!-- /wp:group -->
```

## Resource links

Learn more about [internationalization](https://developer.wordpress.org/apis/handbook/internationalization/) or [Block patterns](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/).

Changelog:

*   **Created** 2022-01-24