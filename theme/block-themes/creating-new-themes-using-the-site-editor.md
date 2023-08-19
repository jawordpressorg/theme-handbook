# Creating new themes using the Site Editor

An alternative to creating themes from scratch using code is to make updates to an existing theme in the [Site Editor](https://wordpress.org/support/article/site-editor/) and export the changes.

The export functionality copies your theme files into a downloadable zip file. The feature has limited support in WordPress 5.9 and improved support in WordPress 6.0:

*   **5.9:** The Site Editor exports the templates and template parts but not the [theme.json](https://developer.wordpress.org/themes/advanced-topics/theme-json/) configuration file. The export includes the file structure but not the color palette or block settings.
*   **6.0:** The Site Editor exports a complete copy of your active theme, including changes to templates and styles. This theme is ready to be installed and activated.

You can use this method to speed up theme creation if you are familiar with the block editor but not the [block markup](https://developer.wordpress.org/themes/block-themes/templates-and-template-parts/#block-markup).

## Editing an existing theme

The Site Editor is only available when a block theme is active. Because of that, you must first install and activate a block theme that you use as a base for your new theme.  
– Make sure that the theme you use [has a license compatible with GPL](https://developer.wordpress.org/themes/getting-started/wordpress-licensing-the-gpl/) so that you have the legal right to make changes and transform it into your own theme. You can use [any block theme from the WordPress theme directory](https://wordpress.org/themes/tags/full-site-editing/) as your base theme.

Optionally, you can download the *Empty theme* from the [theme experiments GitHub repository](https://github.com/WordPress/theme-experiments/tree/master/emptytheme). You do not need to remove any excess templates or block styles from this theme because the theme is nearly empty.

Only user roles with the correct capabilities (for example, administrator) can access the templates.

In the Site Editor, click on the WordPress icon or Site icon in the top toolbar to open the list of templates or template parts:

[![The Site Editor Template list.](https://developer.wordpress.org/files/2022/01/FSE-site-editor-template-list-1024x441.png)](https://developer.wordpress.org/files/2022/01/FSE-site-editor-template-list.png)

Click on the name of the template or template part to open it in the Site Editor.  
You can also use the Add New button to create templates.  
Once inside the Site Editor, you can start editing by moving, deleting, or replacing the blocks.

## Exporting

To export changes you have made in the Site Editor, open the More tools & options menu and select export. Exporting will download a file called theme-name.zip (If you are using WordPress 5.9, the file name is edit-site-export.zip). Depending on the size of the theme, the export can take a few seconds.

[![](https://developer.wordpress.org/files/2022/01/site-editor-export.png)](https://developer.wordpress.org/files/2022/01/site-editor-export.png)

## Creating a theme from the exported files

### Using WordPress 5.9

To convert the export to a complete WordPress theme, you must add the minimum required files.

Step 1: Rename the `theme` folder to your theme name. If your theme is called “My first theme” the name of the folder should be `my-first-theme.`

Next, please [create a new style.css file](https://developer.wordpress.org/themes/basics/main-stylesheet-style-css/) and place it in the root folder.

Create an empty index.php file and place it in the root folder.

Your theme should now have the following structure:

```
parts(dir)
templates(dir)
index.php
style.css
```

You can now activate the new theme, and you have created a theme *almost* without using code.  
You can add a theme.json file, block patterns, and block styles to improve the theme further.

### Using WordPress 6.0

The exported theme is a copy of the active theme. If you install the zip file through the Add Themes page in the WordPress admin area, you will be asked if you want to replace the current theme.  
**Do not do this if you have edited someone else’s theme** since you will lose your changes if the original theme is updated.  
Instead, rename the theme to make it your own. How to rename the theme depends on how the original theme is built. You need to update:

*   The theme folder name
*   The theme name and text-domain inside style.css
*   The author name and links in style.css and readme.txt

In most cases, you can use a *search and replace* tool and replace the following:

*   Text domain in translation strings
*   Prefixes for PHP functions
*   Slugs used in the patterns block

Examples:

```
if ( ! function_exists( 'twentytwentytwo_support' ) ) :

	/**
	 * Sets up theme defaults and registers support for various WordPress features.
	 *
	 * @since Twenty Twenty-Two 1.0
	 *
	 * @return void
	 */
	function twentytwentytwo_support() {

		// Add support for block styles.
		add_theme_support( 'wp-block-styles' );

		// Enqueue editor styles.
		add_editor_style( 'style.css' );

	}

endif;
add_action( 'after_setup_theme', 'twentytwentytwo_support' );
```

Should be changed to

```
if ( ! function_exists( 'my_theme_name_support' ) ) :

	/**
	 * Sets up theme defaults and registers support for various WordPress features.
	 *
	 * @since My theme name 1.0
	 *
	 * @return void
	 */
	function my_theme_name_support() {

		// Add support for block styles.
		add_theme_support( 'wp-block-styles' );

		// Enqueue editor styles.
		add_editor_style( 'style.css' );

	}

endif;
add_action( 'after_setup_theme', 'my_theme_name_support' );
```

```
<!-- wp:pattern {"slug":"twentytwentytwo/hidden-heading-and-bird"} /-->
```

Should be changed to

```
<!-- wp:pattern {"slug":"my-theme-name/hidden-heading-and-bird"} /-->
```

## Sharing your new theme

If you want to share your theme with others, you first need to complete the rename.  
You also need to edit template files and remove image IDs and navigation menu references that are unique to your website.  
This is because if your theme refers to a specific navigation menu that only exists on your website, or to an image in your media library, these will not display correctly.

```
<!-- wp:navigation {"ref":123} /—>
```

Should be

```
<!-- wp:navigation /-->
```

Finally, add credits to the original theme and the theme author.

Learn how to share your theme on WordPress.org in the chapter: [Releasing Your Theme](https://developer.wordpress.org/themes/releasing-your-theme/).

Changelog:

*   **Created** 2022-01-20
*   Updated 2022-05-19