# Settings Reference

The document is a reference to the available settings properties that you can configure via the `settings` object in `theme.json`. Each of the settings has an in-depth guide on how to use it within the [Settings documentation](https://developer.wordpress.org/themes/global-settings-and-styles/settings/).

## Appearance Tools

`settings.appearanceTools` is a top-level property with no sub-properties nested beneath it. It is documented at [Settings: Appearance Tools](https://developer.wordpress.org/global-settings-and-styles/settings/appearance-tools/).

| Property | Type | Default |
| --- | --- | --- |
| `appearanceTools` | boolean | `false` |

## Border

`settings.border` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Border](https://developer.wordpress.org/global-settings-and-styles/settings/border/).

| Property | Type | Default |
| --- | --- | --- |
| `color` | boolean | `false` |
| `radius` | boolean | `false` |
| `style` | boolean | `false` |
| `width` | boolean | `false` |

Enabling any one of the `color`, `style`, or `width` settings will automatically enable the other two since the properties are linked together.

## Color

`settings.color` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Color](https://developer.wordpress.org/global-settings-and-styles/settings/color/).

| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `background` | boolean | `true` | — |
| `custom` | boolean | `true` | — |
| `customDuotone` | boolean | `true` | — |
| `customGradient` | boolean | `true` | — |
| `defaultDuotone` | boolean | `true` | — |
| `defaultGradients` | boolean | `true` | — |
| `defaultPalette` | boolean | `true` | — |
| `duotone` | array <object> | `array` | `colors`, `name`, `slug` |
| `gradients` | array <object> | `array` | `gradient`, `name`, `slug` |
| `link` | boolean | `false` | — |
| `palette` | array <object> | `array` | `color`, `name`, `slug` |
| `text` | boolean | `true` | — |

## Custom

`settings.custom` is an object that supports any number of nested custom properties, as shown in the below table. It is documented at [Settings: Custom](https://developer.wordpress.org/global-settings-and-styles/settings/custom/).

| Property | Type | Default |
| --- | --- | --- |
| `custom.<custom>` | any | — |

## Dimensions

`settings.dimensions` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Dimensions](https://developer.wordpress.org/global-settings-and-styles/settings/dimensions/).

| Property | Type | Default |
| --- | --- | --- |
| `minHeight` | boolean | `false` |

## Layout

`settings.layout` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Layout](https://developer.wordpress.org/global-settings-and-styles/settings/layout/).

| Property | Type | Default |
| --- | --- | --- |
| `contentSize` | string | `""` |
| `wideSize` | string | `""` |

## Lightbox

`settings.lightbox` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Lightbox](https://developer.wordpress.org/global-settings-and-styles/settings/lightbox/).

| Property | Type | Default |
| --- | --- | --- |
| `allowEditing` | boolean | `true` |
| `enabled` | boolean | `false` |

This setting is only available as of WordPress 6.4 and is specific to the core Image block (`core/image`).

## Position

`settings.position` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Position](https://developer.wordpress.org/global-settings-and-styles/settings/position/).

| Property | Type | Default |
| --- | --- | --- |
| `sticky` | boolean | `false` |

## Shadow

`settings.shadow` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Shadow](https://developer.wordpress.org/global-settings-and-styles/settings/shadow/).

| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `defaultPresets` | boolean | `true` |  |
| `presets` | array <object> | `array` | `name`, `shadow`, `slug` |

## Spacing

`settings.spacing` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Spacing](https://developer.wordpress.org/global-settings-and-styles/settings/spacing/).

| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `blockGap` | boolean|null | `null` | — |
| `customSpacingSize` | boolean | `true` | — |
| `margin` | boolean | `false` | — |
| `padding` | boolean | `false` | — |
| `spacingScale` | object | `object` | `operator`, `increment`, `steps`, `mediumStep`, `unit` |
| `spacingSizes` | array <object> | `array` | `name`, `size`, `slug` |
| `units` | array <string> | `[ "px", "em", "rem", "vh", "vw", "%" ]` | — |

## Typography

`settings.typography` is an object that supports the nested properties listed in the below table. It is documented at [Settings: Typography](https://developer.wordpress.org/global-settings-and-styles/settings/typography/).

| Property | Type | Default | Props |
| --- | --- | --- | --- |
| `customFontSize` | boolean | `true` | — |
| `dropCap` | boolean | `true` | — |
| `fontFamilies` | array <object> | `array` | `fontFace`, `fontFamily`, `name`, `slug` |
| `fontSizes` | array <object> | `array` | `fluid`, `name`, `size`, `slug` |
| `fontStyle` | boolean | `true` | — |
| `fontWeight` | boolean | `true` | — |
| `fluid` | boolean | `false` | — |
| `letterSpacing` | boolean | `true` | — |
| `lineHeight` | boolean | `false` | — |
| `textColumns` | boolean | `false` | — |
| `textDecoration` | boolean | `true` | — |
| `textTransform` | boolean | `true` | — |
| `writingMode` | boolean | `false` | — |

## Use Root Padding Aware Alignments

`settings.useRootPaddingAwareAlignments` is a top-level property with no sub-properties nested beneath it. It is documented at [Settings: Use Root Padding Aware Alignments](https://developer.wordpress.org/global-settings-and-styles/settings/use-root-padding-aware-alignments/).

| Property | Type | Default |
| --- | --- | --- |
| `useRootPaddingAwareAlignments` | boolean | `false` |

This setting works together with `styles.spacing.padding` in `theme.json`. If enabled, `styles.spacing.padding` must be an object that defines the `top`, `right`,  `bottom`, and `left` styles separately.