# Converting a classic theme to a block theme

While you can find many [benefits](https://developer.wordpress.org/themes/block-themes/#the-benefits-of-block-themes), there are a few potential issues to consider when converting a classic theme to a block theme.

*   Converting a classic theme may affect child themes. Consider the potential impacts before converting.
*   theme.json requires WordPress version 5.8 or later. Consequently, the support for Internet Explorer 11 was dropped when WordPress 5.8 was released. If your classic theme supports IE11, converting to a block theme potentially impacts the theme’s appearance.

## Gradually adopting the Site Editing features

There are several ways to slowly adopt the Site Editing features on a classic theme.

**Universal themes**
A universal theme is a block theme that has the Customizer options. The Customizer is not available as a default on a block theme, but you can enable it by adding `customize_register` on functions.php. Learn more about [customize\_register](https://developer.wordpress.org/reference/hooks/customize_register/).

**Hybrid themes**
A hybrid theme is a classic theme that adopts the Site Editing features such as [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/) or [template editor.](https://make.wordpress.org/core/2021/06/16/introducing-the-template-editor-in-wordpress-5-8/) For example, you can enable color pallets or set default content width by simply adding theme.json on your classic theme.

Note: Adding a theme.json enables global styles, but it does not enable the styles interface.

## Enabling block features

### Adding theme.json in classic themes

theme.json manages global styles and also per block. In addition, it consolidates all `add_theme_support`. When using theme.json, there is no need to call add\_theme\_support in functions.php. theme.json can be added to classic themes by creating theme.json in the root directory. Note that theme.json requires WordPress version 5.8 or later. Learn more about [theme.json](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/).

### Adding block patterns in classic themes

Block patterns are preset layouts that are made up of blocks. They can be inserted anywhere on a site, including the header and footer. For example, when a classic theme offers users a choice to add a sidebar, traditionally a theme provides a one-column layout or a two-column layout via the Customizer. Block patterns can offer the same options using block markup. Learn more about [how to add block patterns](https://developer.wordpress.org/block-editor/reference-guides/block-api/block-patterns/).

### Enabling template editor

There are several ways to enable the template editor:

*   Adding theme.json
*   Adding `add_theme_support( 'block-templates' );`

### Disabling template editor

To use theme.json without the template editor, theme authors can opt-out of this feature by removing the `block-templates` theme support:

```php
remove_theme_support( 'block-templates' );
```

### Adding block template parts in classic themes

Since WordPress 6.1, classic themes can add block-based template parts. The feature allows end-users to customize their output via Appearance > Template Parts in the WordPress admin. Theme authors must register support to enable the feature:

```php
add_theme_support( 'block-template-parts' );
```

From that point, developers can add template parts to their theme’s `parts` folder. For details on creating parts, see the [template parts for block themes](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/#block-c5fa39a2-a27d-4bd2-98d0-dc6249a0801a) handbook page.

In general, a PHP-based template part that is included via `get_template_part( $name )` can be replaced with a call to `block_template_part( $name )`. It only needs a corresponding `parts/{$name}.html` file and block markup. Headers, footers, and even sidebars can be turned into a block-ready area for users.

**Important!** Classic themes must add opening and closing `<html>` and `<body>` tags along with the appropriate `wp_head()`, `wp_body_open()`, and `wp_footer()` hook calls as usual. These are easy to overlook when replacing header and footer template parts.

### Customizer options

Creating a templates directory and adding an index.html inside it enables the template editor in the post editor, and the Site Editor under the Appearance menu in the admin area. However, this results in hiding the Customizer menu.

Note: You can restore the Customizer by adding [customize\_register](https://developer.wordpress.org/reference/hooks/customize_register/). This method is considered as a Universal theme or Hybrid theme. The universal theme works with Customizer and the Site Editor.

## Additional resources

*   [State of the Customizer with block themes in WordPress 5.9](https://make.wordpress.org/core/2022/01/07/state-of-the-customizer-with-block-themes-in-wordpress-5-9/)
*   [Block-styles loading enhancements in WordPress 5.8](https://make.wordpress.org/core/2021/07/01/block-styles-loading-enhancements-in-wordpress-5-8/)
*   [Should we update or retire existing themes?](https://fullsiteediting.com/lessons/adding-full-site-editing-features-to-classic-themes/#h-should-we-update-or-retire-existing-themes)
*   [Sharing Approaches for FSE Feature Adoption](https://nomad.blog/2021/09/29/sharing-approaches-for-fse-feature-adoption/)
*   [What Happens to the Customizer When a Block Theme Is Active?](https://wptavern.com/ask-the-bartender-what-happens-to-the-customizer-when-a-block-theme-is-active)

Changelog:

*   **Updated** 2022-09-26 Added block template parts sub-section.
*   **Updated** 2022-02-15 Added information about how to remove the block template theme support.
*   **Created** 2022-01-20
