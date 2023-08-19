# Theme.json

## What is theme.json?

`Theme.json` It is a configuration file for theme styles and block settings.

The feature was added in WordPress version 5.8 and does not work with older versions of WordPress unless you activate the [Gutenberg plugin](https://wordpress.org/plugins/gutenberg/).

Some of the things you can do with theme.json are:

*   Enable or disable features like drop cap, padding, margin, and custom line-height
*   Add multiple color palettes, gradients, and duotones
*   Add font sizes
*   Add default widths for content and wide content
*   Add custom CSS properties
*   Assign template parts to template part areas


When you add theme.json to your theme, the [template editor](https://make.wordpress.org/core/2021/06/16/introducing-the-template-editor-in-wordpress-5-8/) is enabled.

There are important differences between what is available for `theme.json` in WordPress version 5.8 (version 1), WordPress 5.9 and newer (version 2), and the Gutenberg plugin (experimental features).
This page includes information about version 2 of `theme.json`.

**This page is a complement to the [How-to guide](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/) in the block editor handbook and to the [theme.json reference](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference).**

## How to create a theme.json file

**Tip:** When developing your theme.json file, you can disable cache to see your changes applied faster.
Set either [WP\_DEBUG](https://wordpress.org/support/article/debugging-in-wordpress/#wp_debu) or [SCRIPT\_DEBUG](https://wordpress.org/support/article/debugging-in-wordpress/#script_debug) to ‘true’ in your [wp-config.php file.](https://wordpress.org/support/article/editing-wp-config-php/)

Create a new file called `theme.json` inside the root folder of your theme. 

Next, add a pair of curly brackets, and inside the curly brackets, include the version number:

```
{
    "version": 2
}
```

It’s important to include the version attribute; otherwise, the data will be parsed as “version 0”, which differs greatly from the expected behavior outlined here.

There are two main sections:

*   **Settings**, where you define your block controls and color palettes, font sizes, and more.
*   **Styles**, where you apply these colors and font sizes to the website and blocks.

Add the section name, place your settings between the curly brackets, and separate objects with commas:

```
{
    "version": 2,
    "settings": {
          "color": {},
          "typography": {}
    }
}
```

You can target both the website and blocks with settings and styles:

*   Place global, site wide settings at the root level of a section
*   Place block settings inside “blocks”, followed by the block name

```
{
	"version": 2,
	"settings": {
		"color": { ... }, // Global settings
		"blocks": {
			"core/group": {
				"color": { ... }, // Group block color settings
				"typography": { ... } // Group typography settings
			}
		}
	}
}
```

### Preset Values

WordPress uses data from `theme.json` to control the editor’s block settings and create CSS custom properties. An example of this is the color palette. The values are used to provide the user with color palette options and to generate CSS properties that you can use elsewhere in `theme.json` or in the theme’s CSS.

This example shows a color palette with a single black color:

```
{
    "version": 2,
    "settings": {
        "color": {
            "palette": [
                {
                    "name": "Black",
                    "slug": "black",
                    "color": "#000000"
                }
            ]
        }
    }
}
```

This results in the generation of the CSS variable in the body of the website:

`--wp--preset--color--black: #000000;`

This example shows a color palette added only to the paragraph block with a single blue color:

```
{
    "version": 2,
    "settings": {
            "blocks": {
                "core/paragraph": {
                    "color": {
                        "palette": [
                            {
                                "name": "Blue",
                                "slug": "blue",
                                "color": "#0000FF"
                            }
                        ]
                    }
                }
            }
        }
    }
}
```

That example will make available the following CSS variable within the paragraph block element:

`--wp--preset--color--blue: #0000FF;`

## Custom Values

Values stored in the settings.custom area (or `settings.blocks.BLOCKNAME.custom` areas) generates CSS properties that you can use elsewhere in the `theme.json` file or the theme’s CSS.

```
{
    "version": 2,
    "settings": {
            "custom": {
                "fruit": "apple"
            },
            "blocks": {
                "core/paragraph": {
                    "custom": {
                        "fruit": "pear"
                    }
                }
            }
        }
    }
}
```

The above will cause the CSS variable `--wp--custom--fruit` to be created with a value of “apple”. However, the value will be “pear” for the “core/paragraph” elements.

## A theme.json can be added to any theme

Theme.json works with both classic PHP-based themes as well as block themes. Theme.json does not work with the classic editor.

If you add a `theme.json` file to an existing theme, you may need to adjust the theme’s CSS and remove duplicate styles for `theme.json` to work properly.
Additionally, the alignment mechanism for “full” and “wide” blocks works differently with a theme.json present and should be considered.

Note that the settings in `theme.json` replace many of the calls to `add_theme_support()`. The color palette in `theme.json` is the equivalent of `add_theme_support( 'editor-color-palette', …).`
When both are present, the palette from `theme.json` takes precedence.

## Settings

### Color

Each color, gradient, and duotone has three key- and value pairs:

*   **slug**, used in the CSS preset
*   \[**color**, **gradient**, or **colors**\]
*   **name**, the visible name in the editor (optional).

#### Color palette

The color value for the palette item can be any valid CSS color value such as “blue” or a hex color such as “#00FF00”.

When creating a custom color palette in your theme, it is recommended to include colors with the slug base for the background of your site and `contrast` for the main text color.

#### Gradients

You can create gradients with any valid CSS color value and assign them to the “gradient” key. The example below uses the CSS properties generated from the palette.

#### Duotone

Duotone colors are expressed in an array assigned to the “colors” key. They must be hex or rgb color values.

```
{
    "version": 2,
        "settings": {
            "color": {
                "palette": [
                    {
                        "slug": "purple",
                        "color": "#D1D1E4",
                        "name": "Purple"
                    },
                    {
                        "slug": "yellow",
                        "color": "#EEEADD",
                        "name": "Yellow"
                    }
                ],
                "gradients": [
                    {
                        "slug": "purple-to-yellow",
                        "gradient": "linear-gradient(160deg, var(--wp--preset--color--purple), var(--wp--preset--color--yellow))",
                        "name": "Purple to Yellow"
                    }
                ],
                "duotone": [
                    {
                        "slug": "purple-and-yellow",
                        "colors": [ "#D1D1E4", "#EEEADD" ],
                        "name": "Purple and yellow"
                    }
                ]
            }
        }
    }
}
```

### Typography

#### Font size

Font sizes defined in `theme.json` supersede values assigned via the ‘editor-font-sizes’ theme support. They consist of the same three values: `slug`, `size` and `name`.

```
{
	"version": 2,
	"settings": {
		"typography": {
			"fontSizes": [
				{
					"slug": "small",
					"size": "1rem",
					"name": "Small"
				},
				{
					"slug": "medium",
					"size": "1.5rem",
					"name": "medium"
				}
			]
		}
	}
}
```

### Layout

The layout setting enables wide and full-width blocks.

```
{
	"version": 2,
	"settings": {
		"layout": {
			"contentSize": "840px",
			"wideSize": "1100px"
		}
	}
}
```

Note that the alignment mechanism leveraged here is different than what was previously enabled via align-wide theme support. If gradually adopting FSE features within a classic theme, some user’s layouts may change when upgrading the theme. Because classic themes managed their own content width, the editor always displayed wide/full controls for blocks that supported them.

However, the logic for wide/full handling changes when a theme has a `theme.json` file. WordPress then handles the styles for content width. For wide/full alignments to appear, the theme must define the `layout` setting in `theme.json`. The major difference in the handling is that content widths need to be set for each container, and the wide/full controls only appear on children of blocks with a content width set.

There is an open ticket with a [full description of the issue](https://github.com/WordPress/gutenberg/issues/33374) and a pull request for a new [default layout type](https://github.com/WordPress/gutenberg/pull/42763) to address this for users.

### Spacing

Enable custom margin, padding, and custom spacing units:

```json
{
	"version": 2,
	"settings": {
		"spacing": {
			"padding": true,
			"margin": true,
			"units": [ "px", "em", "rem", "vh", "vw", "%" ]
		}
	}
}
```

#### Spacing scale

WordPress generates custom spacing scale by default. Users can select these options for blocks that support margin, padding, and block gap via the editor UI. The default scale has seven steps, as shown in the following table:

| CSS Custom Property | CSS Value | Label |
| --- | --- | --- |
| `–wp–preset–spacing–20` | `0.44rem` | 2X-Small |
| `–wp–preset–spacing–30` | `0.67rem` | X-Small |
| `–wp–preset–spacing–40` | `1rem` | Small |
| `–wp–preset–spacing–50` | `1.5rem` | Medium |
| `–wp–preset–spacing–60` | `2.25rem` | Large |
| `–wp–preset–spacing–70` | `3.38rem` | X-Large |
| `–wp–preset–spacing–80` | `5.06rem` | 2X-Large |

Theme authors can use the custom properties to define default margin, padding, or block gap styles via `theme.json`. The following code shows how to set the top and bottom margin for the core Heading block:

```json
{
    "version": 2,
    "styles": {
        "blocks": {
            "core/heading": {
                "spacing": {
                    "margin": {
                        "top": "var( --wp--preset--spacing--60 )",
                        "bottom": "var( --wp--preset--spacing--40 )"
                    }
                }
            }
        }
    }
}
```

#### Custom spacing scale

WordPress allows theme authors to create a custom spacing scale by providing a set of configuration instructions for generating it. When generated, each step in the scale creates a custom CSS property with the slug of `--wp--preset--spacing--{step}` (steps appear in increments of 10, regardless of their value).

The `spacingScale` object has five sub-settings that themes can configure:

*   **operator:** The operator used to increment the scale. The available options are `+` (addition) and `*` (multiplication). The default value is `*`.
*   **increment:** A number in which to increment the scale by when used in conjunction with the `operator` setting. The default value is `1.5`.
*   **steps:** The total number of steps in the scale. The default value is `7`.
*   **mediumStep:** The medium value of the scale. The default value is `1.5`.
*   **unit:** A valid CSS spacing unit. The available options are `px`, `em`, `rem`, `vh`, `vw`, and `%`. The default value is `rem`.

The following example is a custom scale with five steps that increments by `0.25rem`:

```json
{
    "version": 2,
    "settings": {
        "spacing": {
            "spacingScale": {
                "operator": "+",
                "increment": 0.25,
                "steps": 5,
                "mediumStep": 0.75,
                "unit": "rem"
            }
        }
    }
}
```

**Note #1:** The `mediumStep` value is always assigned to the `--wp--preset--spacing--50` preset when WordPress generates the CSS, and the other preset slugs in the scale extend up/down from this middle number in increments of `10`.

**Note #2:** The spacing scale will never go below `--wp--preset--spacing--10`. For scales with more than 10 steps, the bottom end of the scale will not generate presets because the `mediumStep` is always set to `--wp--preset--spacing--50`.

#### Custom spacing sizes

For theme authors who want more precise control over the spacing options available to users, they can build out the individual spacing sizes instead of using the WordPress spacing scale system. This provides control over the option’s name, size, and slug.

The `spacingSizes` option allows themes to define an array of size objects. Each size object accepts three values:

*   **name:** The human-readable title for the size, which can be translated.
*   **size:** A valid CSS size. This can be a number and unit, a fluid size using `clamp()`, or a reference to another custom CSS property.
*   **slug:** The slug for the size, which will be appended to a generated CSS custom property: `--wp--preset--spacing--{slug}`.

The following example is an example of creating a five-step scale that increments by `0.25rem`. However, theme authors are not limited in how they set up their sizes.

```json
{
    "version": 2,
    "settings": {
        "spacing": {
            "spacingSizes": [
                {
                    "name": "Step 1",
                    "size": "0.25rem",
                    "slug": "10"
                },
                {
                    "name": "Step 2",
                    "size": "0.5rem",
                    "slug": "20"
                },
                {
                    "name": "Step 3",
                    "size": "0.75rem",
                    "slug": "30"
                },
                {
                    "name": "Step 4",
                    "size": "1rem",
                    "slug": "40"
                },
                {
                    "name": "Step 5",
                    "size": "1.25rem",
                    "slug": "50"
                }
            ]
        }
    }
}
```

For theme authors who want to implement fluid spacing sizes, they should use the `spacingSizes` setting instead of `spacingScale`. This allows for the use of custom `clamp()` values.

#### Disabling custom spacing size

Theme authors can force users into using the standardized scale set by the theme. To do this, they must set the `customSpacingSize` setting to `false` (defaults to `true`). This disables the custom spacing option in the editor UI but leaves the control for the theme’s defined sizes available.

```json
{
    "version": 2,
    "settings": {
        "spacing": {
            "customSpacingSize": false
        }
    }
}
```

## Enabling and disabling settings

Within settings, you can enable or disable block controls in the editor.

The following features are enabled by default:

*   Custom colors (The color picker)
*   Custom duotone (The color picker)
*   Custom gradient (The color picker)
*   Custom font size
*   Drop cap

To disable them, you need to set the setting’s value to false.

This example disables the custom color picker for the color palette and gradients:

```
{
	"version": 2,
	"settings": {
		"color": {
			"custom": false,
                        "customGradient": false
                 }
         }
}
```

This example disables dropCap:

```
{
	"version": 2,
	"settings": {
		"typography": {
			"dropCap": false
                 }
         }
}
```

The following features are disabled by default:

*   Link color
*   Padding and margin
*   Custom line-height

To enable them, you need to set the setting’s value to true.

Example:

```
{
	"version": 2,
	"settings": {
		"color": {
			"link": true
                 },
                "typography": {
                         "lineHeight": true
                }
         }
}
```

Or, you can enable `AppearanceTools` to enable these features in one single setting:

*   border: color, radius, style, width
*   color: link
*   spacing: blockGap, margin, padding
*   typography: lineHeight
*   dimensions: minHeight
*   position: sticky

```
{
	"version": 2,
	"settings": {
		"appearanceTools": true,
         }
}
```

## Styles

Just like settings, styles that are applied to the website body are placed on the root level of the styles section.

```
{
    "version": 2,
    "settings": { ... },
    "styles":{
        "color":{
            "background":"var(--wp--preset--color--white)",
            "text":"var(--wp--preset--color--black)"
        },
        "typography":{
            "fontSize":"1.5rem",
            "fontFamily":"var(--wp--preset--font-family--system-fonts)",
            "lineHeight":"1.5"
        },
        "spacing":{
            "margin":{
                "top":"0px",
                "right":"0px",
                "bottom":"0px",
                "left":"0px"
            }
        }
    }
}
```

Styles that are applied to blocks are placed under *styles.blocks.BLOCKNAME*:

```
{
    "version": 2,
    "settings": { ... },
    "styles": {
        "blocks": {
            "core/post-title": {
                "typography": {
                    "fontSize":"var(--wp--preset--font-size--extra-large)"
                }
            },
            "core/paragraph": {
                "typography": {
                    "fontSize":"var(--wp--preset--font-size--normal)"
                }
            }
        }
    }
}
```

### `Theme.json` elements

Blocks can have multiple HTML elements. You can use `elements` to style headings (H1-H6) and links inside blocks.
In this example, background color and padding are added to the read more link inside the post excerpt block:

```
{
    "version": 2,
    "settings": { ... },
    "styles": {
        "blocks": {
            "core/post-excerpt": {
                "elements": {
                    "link": {
                        "color": {
                            "background": "var(--wp--preset--color--light-grey)"
                        },
                        "spacing": {
                            "padding": {
                            "top": "calc(.667em + 2px)",
                            "right": "calc(1.333em + 2px)",
                            "bottom": "calc(.667em + 2px)",
                            "left": "calc(1.333em + 2px)"
                        }
                    }
                }
            }
        }
    }
}
```

## Assigning template parts

You assign default template parts to template areas in the templateParts section.
Add three keys: `name`, the file name of the template part file without the file extension, `area`, the name of the template area, and `title`, the visible name in the editor. There are three template areas to choose from: header, footer, and uncategorized (general).

Example from Twenty Twenty-Two:

```
"templateParts": [
	{
		"name": "header",
		"title": "Header",
		"area": "header"
	},
	{
		"name": "header-large-dark",
		"title": "Header (Dark, large)",
		"area": "header"
	},
	{
		"name": "header-small-dark",
		"title": "Header (Dark, small)",
		"area": "header"
	},
	{
		"name": "footer",
		"title": "Footer",
		"area": "footer"
	}
]
```

## Defining custom templates

In a classic theme, custom page templates are identified with a file header. In a block theme, you can list block templates in the `theme.json` file.
All templates that are listed in the customTemplates section of `theme.json` are selectable in the Site Editor. For templates to be editable in the template editor, the template’s file name needs to be prefixed with the post type (usually `post-` or `page-`).

Add two keys: `name`, the file name of the template part file without the file extension, `title`, the visible name in the editor. There is also an optional setting where you decide which post types that can use the template. The key is `postTypes`, followed by the name of the post type:

```
"customTemplates": [
    {
        "name": "page-home",
        "title": "Page without title"
    },
    {
        "name": "page-contact",
        "title": "Contact",
        "postTypes": [ "page" ]
    }
]
```

## Global Styles variations

A theme can have multiple JSON files for offering different styles at the top-level settings. The option for the additional styles will appear under the Browse Styles in the side editor. When a user selects the additional style, it will overwrite the styles on the default theme.json. There are several requirements to keep in mind.

*   The minimum required WordPress version is 6.0.
*   The default theme.json must be located in the root directory and is required to declare using theme.json version 2.
*   Additional JSON files must be placed in the `/styles` directory.

`Title` can be added to the additional JSON files to label each style variation. The users will see the title on the site editor. If `title` is missing from a JSON file, the file name will be used as the label instead.

With the below example, the users see “Dark” as the label for this style variation in the side editor. Also, in this example, the background and the text color properties will overwrite the default style when a user selects the ‘Dark” style.

```
{
    "version": 2,
    "title": "Dark",
    "styles": {
        "color": {
            "background": "black",
            "text": "white"
        }
    }
}
```

## Resource Links

*   [Theme.json How-to Guide](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/)
*   [Theme.json reference](https://developer.wordpress.org/block-editor/reference-guides/theme-json-reference)

*   **Updated** 2023-2-24 Added color slug recommendations.
*   **Updated** 2023-01-16 Added spacing scale, custom spacing scale, custom spacing sizes, and disabling custom spacing size sections.
*   **Updated** 2022-08-05 Added notes to the Layout section to clarify differences between classic and `theme.json` wide/full layouts.
*   **Updated** 2022-07-13 Added information about enabling WP\_DEBUG to disable cache for theme.json.
*   **Updated** 2022-05-17 Added Global Styles variations.
*   **Updated** 2022-02-15. Added % to spacing units, added information about templateParts and customTemplates.
*   **Created** 2022-02
