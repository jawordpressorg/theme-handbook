# Theme.json

## What is `theme.json`?

`Theme.json` is a configuration file for theme styles and block settings.

The feature was added in WordPress version 5.8 and does not work with older versions of WordPress unless you activate the [Gutenberg plugin](https://wordpress.org/plugins/gutenberg/). There are important differences between what is available for `theme.json` in WordPress version 5.8 and the Gutenberg plugin.

*   Enable or disable features like drop cap, padding, margin, and custom line-height
*   Add multiple color palettes, gradients, and duotones
*   Add font sizes
*   Add default widths for content and wide content
*   Add custom CSS properties

When you add the file to your theme, the [template editor](https://make.wordpress.org/core/2021/06/16/introducing-the-template-editor-in-wordpress-5-8/) is enabled.

Note: Additional detailed documentation and examples for using theme.json with the Gutenberg plugin are available in the block editor handbook.  
[How-to Guide for Global Settings and styles](https://developer.wordpress.org/block-editor/how-to-guides/themes/theme-json/)

## How does `theme.json` work?

`theme.json` uses JSON format to add settings with key- and value pairs. There are two main sections:

*   **Settings**, where you define your block controls and color palettes, font sizes, and more.
*   **Styles**, where you apply these colors and font sizes to the website and blocks.

### Global & Block Level Settings

You can target both global (all of the website) and block-level with both settings and styles.  
For example, you can add gradients to the website but turn them off for paragraph blocks.  
  
Example:

```
{
    "version":1,
    "settings": {
        “customGradient”: true,
            "blocks": {
                "core/paragraph": {
	        “customGradient”: false
                }
            }
        }
    }        
}
```

### Preset Values

WordPress uses some of the data in `theme.json` to control the editor’s block settings and create CSS custom properties. An example of this is the color palette. The values are used to provide the user with color palette options and to generate CSS properties that can be used elsewhere in `theme.json` or in the theme’s CSS.

This example shows a color palette with a single black color:

```
{
    "version": 1,
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

This example shows a color palette added to the paragraph block with a single blue color:

```
{
    "version":1,
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

Values stored in the settings.custom area (or `settings.blocks.BLOCKNAME.custom` areas) are used to generate CSS properties that can be used elsewhere in the `theme.json` file or in the theme’s CSS.

```
{
    "version":1,
    "settings": {
            “custom”: {
                “fruit”: “apple”
            },
            "blocks": {
                "core/paragraph": {
                    "custom": {
                        "fruit": “pear”
                    }
                }
            }
        }
    }        
}
```

The above will cause the CSS variable `--wp--custom--fruit` to be created with a value of “apple”.  However, the value will be “pear” for the “core/paragraph” elements.

## How to create a `theme.json` file?

Create a new file called `theme.json` inside the root folder of your theme. 

Next, add a pair of curly brackets, and inside the curly brackets include the version number:

```
{
    "version": 1
}
```

It’s important to include the “version” attribute; otherwise, the data will be parsed as “version 0”, which differs greatly from the expected behavior outlined here.

Add the section name, place your settings between the curly brackets, and separate objects with commas:

```
{
    "version": 1,
    "settings": {
          "color": {},
          "typography": {}  
    }
}
```

## **A `theme.json` can be added to any theme**

The `theme.json` works with both “classic” PHP-based themes as well as block themes. `Theme.json` does not work with the classic editor.

If you add a `theme.json` file to an existing theme, you may need to adjust the theme’s CSS and remove duplicate styles for `theme.json` to work properly.  
Additionally, the alignment mechanism for “full” and “wide” blocks works differently with a theme.json present and should be considered.

Note that the settings in `theme.json` replace many of the calls to [add\_theme\_support()](https://developer.wordpress.org/reference/functions/add_theme_support/).  
For example the color palette in `theme.json` is the equivalent of add\_theme\_support( ‘editor-color-palette’, …).  
When both are present, the palette from `theme.json` takes precedence.

## Settings

### Color

Each color, gradient, and duotone has three key- and value pairs:

*   **slug**, used in the CSS preset
*   \[**color**, **gradient**, or **colors**\]
*   **name**, the visible name in the editor (optional).

#### Color palette

The color value for the palette item can be any valid CSS color value such as “blue” or a hex color such as “#00FF00”.

#### Gradients

You can create gradients with any valid CSS color value and assign them to the “gradient” key. The example below uses the CSS properties generated from the palette.

#### Duotone

Duotone colors are expressed in an array assigned to the “colors” key.  They must be hex or rgb color values.

```
{
    "version": 1,
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

Font sizes defined in `theme.json` supersede values assigned via the ‘editor-font-sizes’ theme support.  They consist of the same three values: `slug`, `size` and `name`.

```
{
	"version": 1,
	"settings": {
		"typography": {
			"fontSizes": [
				{
					"slug": "small",
					"size": "1rem",
					"name": "Small"
				},
				{
					"slug": "normal",
					"size": "1.25rem",
					"name": "Normal"
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

The layout setting enables wide and full-width blocks, as well as custom width units.  Note that the alignment mechanism leveraged here is different than what was previously enabled via `align-wide` theme support.

```
{
	"version": 1,
	"settings": {
		"layout": {
			"contentSize": "840px",
			"wideSize": "1100px",
			"units": [ "px", "em", "rem", "%", "vw" ]
		}
	}
}
```

### Spacing

Enable custom margin, padding, and custom spacing units:

```
{
	"version": 1,
	"settings": {
		"spacing": {
			"customPadding": true,
			"customMargin": true,
			"units": [ "px", "em", "rem", "vh", "vw" ]
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

Example:

```
{
	"version": 1,
	"settings": {
		"color": {
			"custom": false,
                        "customGradient": false
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
	"version": 1,
	"settings": {
		"color": {
			"link": true
                 },
                "typography": { 
                         "customLineHeight": true
                }
         }
}
```

## Styles

Just like settings, styles that are applied to the website body are placed on the root level of the styles section.

```
{
    "version":1,
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
    "version":1,
    "settings": { ... },
    "styles":{
        "blocks":{
            "core/post-title":{
                "typography":{
                    "fontSize":"var(--wp--preset--font-size--extra-large)"
                }
            },
            "core/paragraph":{
                "typography":{
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
    "version": 1,
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

* * *

Written by @pbking and @poena.