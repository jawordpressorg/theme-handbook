# Internationalization

Text inside Template or Template parts that are HTML files can not be made translatable.

## Using text in block patterns

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

## Text in theme.json and style variation files

WordPress assures that texts in theme.json keys are translation ready. The theme developer does not need to wrap text strings inside gettext functionality like `__()`.

The following keys are translatable in WordPress 6.1:

*   Style variation name
*   Font size name
*   Font family name
*   Color name
*   Gradient name
*   Duotone name
*   Custom template name
*   Template part name

## Resource links

Learn more about [internationalization](https://developer.wordpress.org/apis/handbook/internationalization/) or [Block patterns](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/).

Changelog:

*   **Updated** 2022-11-07 Added information about theme.json
*   **Created** 2022-01-24